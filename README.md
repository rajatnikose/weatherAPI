# weatherAPI


OpenWeatherAPI Testing Framework

A robust testing framework designed to validate the functionality and reliability of the WeatherAPI. This framework leverages the Service Object Model (SOM) structure to efficiently handle the diverse responses from the API, ensuring comprehensive test coverage.

Table of Contents

- [Service Object Model Structure]
- [Framework Components]
  - [Connection Manager]
  - [Data Transfer Objects (DTO)]
  - [Injector]
- [Helper Methods]
  - [IsFeelsLike Helper Method]
  - [Bound Temperature Helpers]
  - [Temperature Comparison Helpers]
  - [Sunset/Sunrise Time Helpers]
  - [City Validation Helpers]
  - [Range Validation Helpers]
  - [Weather Item DTO Validation]
  - [Non-Negative Field Helpers]
- [Usage Instructions]
  - [Setup]
  - [Writing Tests]
- [Available Endpoints]
  - [Variable Declaration]
  - [Before All Tests]
  - [Before Each Test]
  - [Basic Search Test]

 Service Object Model Structure

The Service Object Model (SOM) structure is the architectural backbone of the testing framework. SOM is a design pattern tailored for breaking down services of objects in a REST API. Given the OpenWeatherAPI's variety of responses, SOM ensures that each response type is systematically handled, promoting scalability and maintainability.

 Framework Components

Connection Manager

The `ConnectionManager` class is pivotal for establishing connections to desired API endpoints. It utilizes a `HashMap` that accepts an enum representing the endpoint and returns a `HashMap` containing the combined URL along with the original query parameters.

- Key Features:
  - Manages API endpoint connections.
  - Handles URL construction with query parameters.
  - Supports various endpoints through an enum.

Data Transfer Objects (DTO)

DTO classes are essential for mapping the API's response structure. They identify the data patterns and define classes that encapsulate the data and its types. Each DTO provides getters to access specific fields from the API response.

- Key Features:
  - Represents structured API responses.
  - Provides type-safe access to data fields.
  - Facilitates easy manipulation and testing of response data.

Injector

The `Injector` class acts as a tool to transfer data from the API into the appropriate DTOs. This enables the framework to access and test each field's data effectively.

- Key Features:
  - Injects API response data into DTOs.
  - Ensures data consistency and integrity.
  - Streamlines the testing process by providing structured data access.

 Helper Methods

The framework includes a suite of helper methods designed to validate various aspects of the API responses. These methods enhance test readability and reusability.

 IsFeelsLike Helper Method

- Method Signature: `isFeelsLike{Units}GreaterThanMin()`

 Bound Temperature Helpers

- Method Signature: `isMaxTempGreaterThanZero{Unit}()`

Temperature Comparison Helpers

- Method Signature:`isMinTempLessThanMaxTemp{Unit}()`

 Sunset/Sunrise Time Helpers

- Method Signatures:
  - `is{FieldName}TimeLong()`
  - `is{FieldName}Time()`

 City Validation Helpers

- Method Signature: `isCorrectCity{FieldName}()`

 Range Validation Helpers

- Method Signature: `is{Field}GreaterThan{MinValue}AndLessThan{MaxValue}()`

Weather Item DTO Validation

- Method Signature: `isWeatherItemDTOValid(WeatherItemDTO weatherItemDTO)`
- Description: Validates that the key-value pairs in a `WeatherItemDTO` object match the expected weather codes.
- Parameters: 
  - `WeatherItemDTO weatherItemDTO` – The DTO object to validate.

 Non-Negative Field Helpers

- Method Signature: `is{Field}GreaterThanOrEqualToZero()`
- Fields Supported: RainH1, RainH3, SeaLevel, WindSpeed

 Usage Instructions

 Setup

1. Clone the Repository:
   bash
   git clone
   
2. Build the Framework:
   - Use your preferred build tool (e.g., Maven, Gradle) to load and build the testing framework.

Writing Tests

1. Declare Variables:
   - Initialize the necessary variables, including the `HashMap` for parameters and the `ResponseDTO` for storing API responses.
  
2. Instantiate Parameters:
   - Ensure that the parameters are set up and ready for use.
 
3. Setup and Teardown:
   - Before All Tests:
     - Perform any global setup required before running tests.
     
   - Before Each Test:
     - Reset the `ConnectionManager` to prevent data leakage between tests.
    
4. Select Parameters and Execute Test:
   - Choose the desired parameters and execute the API call.
   
 Available Endpoints

The `ENDPOINTS` enum within the `ConnectionManager` defines the available API endpoints:

- WEATHER_Q: Search without specifying a specific query.
- WEATHER_CITY_ID: Search using the city ID as the parameter.
- WEATHER_ZIP: Search using the ZIP code or partial ZIP code as the parameter.
- BOX: Work in Progress (WIP).
