# Serverless Registration Form (AWS Lambda)

This repository contains the code and steps to build a **serverless registration form** using AWS services. The application captures user input from a web form and processes it entirely through managed cloud services, without managing any servers.

---

## Architecture Overview

The solution uses the following AWS services:

- **Amazon API Gateway** – Exposes a REST endpoint for the registration form submission.
- **AWS Lambda** – Backend logic to validate and process form data.
- **Amazon DynamoDB / S3** – Stores submitted registration data (depending on your chosen implementation).
- **Amazon SES (optional)** – Sends confirmation or notification emails after successful submission.
- **Amazon CloudWatch** – Monitors logs and metrics for the Lambda function and API Gateway.

---

## Features

- Fully serverless backend for handling registration submissions.
- Simple HTML/CSS/JavaScript frontend form.
- Input validation and error handling in the Lambda function.
- Persistent storage of form submissions.
- Easy to extend with additional fields or integrations.

---

## Prerequisites

- AWS account with permissions to create:
  - API Gateway REST APIs
  - Lambda functions
  - DynamoDB tables or S3 buckets
  - (Optional) SES configuration for emails
- Node.js or Python runtime installed locally (depending on the Lambda implementation in this repo).
- AWS CLI configured with appropriate credentials (optional but recommended).

---

## Deployment Steps (High Level)

1. **Create the data store**  
   - DynamoDB table or S3 bucket for storing registration records.

2. **Create the Lambda function**  
   - Upload the function code from this repository.
   - Configure environment variables (e.g., table name, region, email sender).

3. **Configure API Gateway**  
   - Create a REST API with a POST endpoint (e.g., `/register`).
   - Integrate the endpoint with the Lambda function as a proxy or custom integration.
   - Enable CORS if the form is hosted on a different domain.

4. **Host the frontend**  
   - Serve the HTML/JS registration form (locally, S3 static hosting, or any web server).
   - Point the form’s `action`/AJAX URL to the API Gateway endpoint.

5. **Test the workflow**  
   - Submit the form and verify:
     - Lambda executes successfully.
     - Data is stored in DynamoDB/S3.
     - (Optional) Email notifications are sent.

---

## Project Structure

- `Serverless-Application-Lambda-b1/`  
  Contains the Lambda function code, configuration files, and frontend assets for the registration form.

*(Adjust filenames and paths to match your actual project layout.)*

---

## Future Enhancements

- Add authentication (e.g., Amazon Cognito) to protect admin views.
- Build an admin dashboard to list and export registrations.
- Add validation and rate limiting at API Gateway level.
- Integrate with additional services (SNS, Step Functions, etc.) for more complex workflows.

---

## License

This project is intended for learning and demonstration purposes. You may adapt or extend it for your own use.
