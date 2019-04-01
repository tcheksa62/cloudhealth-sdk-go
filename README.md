[![GoDoc](http://img.shields.io/badge/godoc-reference-blue.svg)](https://godoc.org/github.com/nextgenhealthcare/cloudhealth-sdk-go)
[![Go Report Card](https://goreportcard.com/badge/github.com/nextgenhealthcare/cloudhealth-sdk-go)](https://goreportcard.com/report/github.com/nextgenhealthcare/cloudhealth-sdk-go)

# CloudHealth API in Go

A Go wrapper for the [CloudHealth Cloud Management Platform](https://www.cloudhealthtech.com/) API.

## Getting Started

Run the following command to retrieve the SDK:

```bash
go get -u github.com/nextgenhealthcare/cloudhealth-sdk-go
```

You will also need an API Key from CloudHealth. For more information, see [Getting Your API Key](http://apidocs.cloudhealthtech.com/#documentation_getting-your-api-key)

```go
import cloudhealth "github.com/nextgenhealthcare/cloudhealth-sdk-go"

client, _ := cloudhealth.NewClient("api_key", "https://chapi.cloudhealthtech.com/v1/")

account, err := client.GetSingleAwsAccount(1234567890)
if err == cloudhealth.ErrAwsAccountNotFound {
	log.Fatalf("AWS Account not found: %s\n", err)
}
if err != nil {
	log.Fatalf("Unknown error: %s\n", err)
}

log.Printf("AWS Account %s\n", account.Name)
```

## Available Endpoints

| Endpoint | Method | Description | Status |
| -- | -- | -- | -- |
| `/aws_accounts` | `POST` | Enable AWS Account | :heavy_check_mark: |
| `/aws_accounts` | `GET` | AWS Accounts in CloudHealth  | :heavy_check_mark: |
| `/aws_accounts/:id` | `GET` | Single AWS Account | :heavy_check_mark: |
| `/aws_accounts/:id` | `PUT` | Update Existing AWS Account | :heavy_check_mark: |
| `/aws_accounts/:id` | `DELETE` | Delete AWS Account | :heavy_check_mark: |
| `/aws_accounts/:id/generate_external_id` | `GET` | Get External ID | :heavy_check_mark: |
| `/customers` | `POST` | Create Partner Customer  | :heavy_check_mark: |
| `/customers/:id` | `PUT` | Modify Existing Customer | :heavy_check_mark:  |
| `/customers/:id` | `DELETE` | Delete Existing Customer  | :heavy_check_mark: |
| `/customers/:id` | `GET` | Get Single Customer | :heavy_check_mark: |
| `/customers` | `GET` | Get All Customers | :heavy_check_mark: |
| `/customer_statements` | `GET` | Statement for Single Customer | :heavy_check_mark: |
| `/customer_statements` | `GET` | Statements for All Customers | :heavy_check_mark: |
| `/aws_account_assignments` | `POST` | Create AWS Account Assignment |  |
| `/aws_account_assignments` | `GET` | Read All AWS Account Assignments |  |
| `/aws_account_assignments/:id` | `GET` | Read Single AWS Account Assignment |  |
| `/aws_account_assignments/:id` | `PUT` | Update AWS Account Assignment |  |
| `/aws_account_assignments/:id` | `DELETE` | Delete AWS Account Assignment |  |

## Contributing

Any and all contributions are welcome. Please don't hesitate to submit an issue or pull request.

## Roadmap

The initial release is focused on being consumed by a Terraform provider in AWS environments such as support for managing AWS Accounts in CloudHealth. Eventually, we plan to introduce support for perspectives and other vendor integrations such as Datadog.


## Development

Run unit tests with `make test`.
