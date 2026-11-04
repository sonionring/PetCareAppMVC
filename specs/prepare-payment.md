# Feature: Prepare payment details

## 1. User goal

Pet owners want to prepare payment details for a pet service.

## 2. Scope

The mock endpoint accepts a selected service and returns its server-defined price and a payment-ready status.

The mock endpoint does not require login. Charging money, integrating a payment gateway, creating new database tables, and adding new pages are out of scope.

## 3. Request

Use `GET /payments/prepare/:serviceId` to request payment preparation for a service, for example: `GET /payments/prepare/2`.

## 4. Service catalogue

The mock catalogue contains:

- ID 1: Vaccination — price 35
- ID 2: Pet Grooming — price 50
- ID 3: Boarding — price 80

The server-side catalogue is the source of truth for service prices; the client does not choose the price.

## 5. Successful response

For a valid service, return HTTP `200 OK` with JSON containing the service ID, service name, amount, currency `"sgd"`, and status `"READY_FOR_PAYMENT"`.

## 6. Unsuccessful response

If the selected service does not exist, return HTTP `404 Not Found` with JSON: `{"error":"Service not found"}`.

## 7. Acceptance criteria

- AC1: `GET /payments/prepare/:serviceId` accepts a service selection without requiring login for this classroom mock endpoint.
- AC2: The server uses its mock catalogue to determine the selected service's amount: Vaccination 35, Pet Grooming 50, or Boarding 80.
- AC3: A valid service returns HTTP `200` with its ID, name, server-defined amount, currency `"sgd"`, and status `"READY_FOR_PAYMENT"`.
- AC4: An unknown service returns HTTP `404` with `{"error":"Service not found"}`.
- AC5: The endpoint does not charge money, use a payment gateway, create new database tables, or add new pages.
- AC6: The service amount is determined by the server, not supplied by the client.

## 8. Open questions

- None for this classroom mock endpoint.