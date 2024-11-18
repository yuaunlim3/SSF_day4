# Use Eclipse Temurin JDK 23 image
FROM eclipse-temurin:23-jdk

LABEL maintainers="yuaunlim"

# Set working directory inside the container
WORKDIR /app

# Copy Maven wrapper and pom.xml
#Every line is like a commit in git
COPY mvnw . 
COPY pom.xml . 

# Copy the source and Maven wrapper directory
COPY src src
COPY .mvn .mvn

# Build the application (skipping tests for faster build)
RUN chmod a+x ./mvnw && ./mvnw package -Dmaven.test.skip=true


# Set default port for the application
ENV PORT=8080

# Expose the defined port (for use in Railway or other environments)
EXPOSE ${PORT}

# Run the application using the generated JAR file
ENTRYPOINT ["java", "-jar", "target/week1Work2-0.0.1-SNAPSHOT.jar"]
