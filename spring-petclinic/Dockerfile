# Use a Maven image to build the application
FROM maven:3.8.4-openjdk-11-slim AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Use an OpenJDK image to run the application
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=build /app/target/spring-petclinic.jar /app/spring-petclinic.jar
ENTRYPOINT ["java", "-jar", "spring-petclinic.jar"]
