# Axon Demo

A small demo application that shows CQRS and event sourcing with Axon Framework in a Kotlin Spring Boot service.

## What it does

The application models a customer domain:

- A customer aggregate handles commands to register a customer and change a password. It applies the matching domain events.
- A projection listens to those events and keeps a read model of customers in a relational database using JPA.
- A GraphQL API sends commands through the Axon command gateway. It answers queries through the Axon query gateway.

## Main technologies

- Kotlin on Java 17
- Spring Boot with Spring for GraphQL, Spring Web and Spring Data JPA
- Axon Framework with the Kotlin extension. It runs without Axon Server and uses the database-backed event store.
- PostgreSQL, provided locally through Docker Compose
- Gradle with the Kotlin DSL
- Axon test fixtures and JUnit for testing the aggregate

## Structure

- Application entry point: the Spring Boot application class
- Customer domain: the aggregate, commands, events and query definitions
- Customer projection: the JPA entity, repository and event and query handlers for the read model
- Customer controller: GraphQL query and mutation mappings
- Resources: the application configuration and the GraphQL schema
- Tests: an application context test and aggregate tests that use the Axon test fixture
- Docker Compose file: a local PostgreSQL instance

## Status

This is demo and learning material. It is not actively maintained. The projection for password changes is not finished: its handler is commented out.