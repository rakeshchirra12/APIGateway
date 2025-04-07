# API Gateway

## Overview
This project is a Spring Boot application that serves as an API Gateway. It routes requests to various microservices using Spring Cloud Gateway and integrates with Eureka for service discovery.

## Project Structure
- `src/main/java/com/gateway/apigateway/ApiGatewayApplication.java`: Main class to bootstrap the API Gateway application.
- `src/main/resources/application.properties`: Configuration file for the API Gateway.

## Technologies Used
- Java
- Spring Boot
- Spring Cloud Gateway
- Eureka
- Maven

## Configuration
The `application.properties` file contains the configuration for the API Gateway, including service discovery and route definitions.

### Example Configuration
```ini
spring.application.name=APIGateway
server.port=8084
logging.level.org.springframework=TRACE

eureka.client.registerWithEureka=true
eureka.client.fetch-registry=true
eureka.client.serviceUrl.defaultZone=${EUREKA_URI:http://localhost:8761/eureka}

spring.cloud.gateway.routes[0].id=product-service
spring.cloud.gateway.routes[0].predicates[0]=Path=/productservice/**
spring.cloud.gateway.routes[0].uri=lb://PRODUCTSERVICE
