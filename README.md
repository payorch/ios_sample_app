# iOS-SDK Sample app
## Change Log
- Separated Swift sample code to separate project and integrated XCFramework.

## Introduction
The purpose of the iOS Software Development Kit (iOS SDK) Integration guide is to serve as a technical documentation for merchants that want to integrate with Geidea and want to use the Payment Gateway services with their systems. When merchants integrate with the iOS SDK they will be able to send parameters from their iOS App when a client is triggering a payment and visualize Geidea Payment SDK for their clients to use to process an online payment.

# Getting Started
## Requirements
- Minimum iOS version: 11.0
- Swift 4.0, 4.2, 5.X or Objective C

## Setup
- Drag GeideaPaymentSDK.XCFramework to your Frameworks folder.
- Add it your target: General -> Frameworks, Libraries and and Embedded Content.
- Choose “Embed & Sign” option on Embed tab
- If your application is Objective C app perform an additional step: Build settings -> Build Options -> Always Embed Swift Standard Libraries set YES

## Configuration
1. import the SDK
```swift
import GeideaPaymentSDK
```
2. Add your merchant credentials (Merchant Public Key and API password) with
```swift
GeideaPaymentAPI.setCredentials(withMerchantKey: <YOUR_MERCHANT_KEY>, andPassword: <YOUR_PASSWORD>)
```
3. You can check if there credentials already stored with the GeideaPaymentAPI.isCredentialsAvailable(). It is only important to be stored prior to using the SDK.
4. To verify your merchant key and config
```swift
 GeideaPaymentAPI.getMerchantConfig(completion:{ response, error in
    //verify the response
 })
```
5. For making payments use pay method on the SDK
```swift
GeideaPaymentAPI.pay(theAmount amount: GeideaPaymentSDK.GDAmount, 
                    withCardDetails cardDetails: GeideaPaymentSDK.GDCardDetails, 
                    initializeResponse: GeideaPaymentSDK.GDInitiateAuthenticateResponse? = nil, 
                    config: GeideaPaymentSDK.GDConfigResponse?, 
                    isHPP: Bool = false, 
                    showReceipt: Bool, 
                    andTokenizationDetails tokenizationDetails: GeideaPaymentSDK.GDTokenizationDetails?,
                    andPaymentIntentId paymentIntentId: String? = nil, 
                    andCustomerDetails customerDetails: GeideaPaymentSDK.GDCustomerDetails?, 
                    orderId: String? = nil, 
                    paymentMethods: [String]? = nil, 
                    dismissAction: ((GeideaPaymentSDK.GDCancelResponse?, GeideaPaymentSDK.GDErrorResponse?) -> Void)? = nil, 
                    navController: UIViewController, 
                    completion:{ response, error in

                        // handle response for payment success

                    })
   ```

