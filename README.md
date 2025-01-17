# Stream API Performance

A performance testing tool for streaming APIs. This package allows you to perform concurrent requests to a specified API endpoint or send requests in a scattered format over a given span of time, log the results, and generate summary statistics, including average first chunk response time, average completion time, failure and success.

## Description

The Stream API Performance package is designed to help developers test the performance of their streaming APIs. It allows for configurable concurrent requests, logs detailed metrics for each request, and provides summary statistics once the test is complete. 

## Installation

To install the package, use the following command:

```sh
npm install streamapiperformance

```

## Usage

```bash
import StreamAPIPerformance from "streamapiperformance";

// Define the configuration for the test
const StreamAPIPerformanceConfig = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://your-api-endpoint.com/api/v1/responses',
  headers: {
    accept: 'text/event-stream, text/event-stream',
  },
  payload: { 
  }
};

const tester = new StreamAPIPerformance('request_logs.csv', 'summary.csv', StreamAPIPerformanceConfig);

// Execute concurrent requests
tester.executeConcurrentRequests(750, 30); 
// This will send 750 requests in 30 minute. Meaning all 750 requests will be scattered over the interval of 30 min. If you want to send all request at the same time set minute paramter as 0

```
## StreamAPIPerformanceConfig Configuration

- **`method`**: The HTTP method to use. Must be one of `'post' | 'get' | 'put' | 'delete' | 'patch'`. **(Required)**
- **`url`**: The URL for the streaming API. **(Required)**
- **`headers`**: Headers to include in the request. **(Required)**
- **`maxBodyLength`**: Optional. Maximum size of the request body in bytes.
- **`payload`**: Optional. The body of the request.

## Reporting
After the test execution, a summary report will be generated in the specified summary file path, providing the following details:

1. Total number of requests
2. Average time to the first chunk of the response \n
3. Average total completion time of the requests
4. Total number of passed and failed requests

## Contributions
Feel free to submit issues or pull requests for improvements or bug fixes.

