# Orders
(*Orders*)

## Overview

The orders endpoints.

### Available Operations

* [CreateOrder](#createorder) - Create an order.

## CreateOrder

Create an order for a drink.

### Example Usage

```go
package main

import(
	"github.com/speakeasy-sdks/template-speakeasy-bar/pkg/models/shared"
	templatespeakeasybar "github.com/speakeasy-sdks/template-speakeasy-bar"
	"context"
	"log"
)

func main() {
    s := templatespeakeasybar.New(
        templatespeakeasybar.WithSecurity("<YOUR_API_KEY_HERE>"),
    )


    requestBody := []shared.OrderInput{
        shared.OrderInput{
            ProductCode: "APM-1F2D3",
            Quantity: 26535,
            Type: shared.OrderTypeDrink,
        },
    }

    var callbackURL *string = templatespeakeasybar.String("<value>")

    ctx := context.Background()
    res, err := s.Orders.CreateOrder(ctx, requestBody, callbackURL)
    if err != nil {
        log.Fatal(err)
    }
    if res.Order != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                    | Type                                                         | Required                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `ctx`                                                        | [context.Context](https://pkg.go.dev/context#Context)        | :heavy_check_mark:                                           | The context to use for the request.                          |
| `requestBody`                                                | [][shared.OrderInput](../../pkg/models/shared/orderinput.md) | :heavy_check_mark:                                           | N/A                                                          |
| `callbackURL`                                                | **string*                                                    | :heavy_minus_sign:                                           | The url to call when the order is updated.                   |


### Response

**[*operations.CreateOrderResponse](../../pkg/models/operations/createorderresponse.md), error**
| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.APIError | 5XX                | application/json   |
| sdkerrors.SDKError | 4xx-5xx            | */*                |
