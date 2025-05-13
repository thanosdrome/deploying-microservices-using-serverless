# Deploying Python and Node.js microservices using serverless (IBM Code Engine)


## Project Scenario

This project involves the deployment and integration of a microservices-based product comparison application developed for CheckNBuy. The application is composed of multiple backend microservices, each handling specific functionality.

Two key microservices have been deployed:

Product Details Service – Provides detailed information about various products.

Dealer Pricing Service – Supplies dealer-specific pricing data for the listed products.

Both services have been deployed using a serverless approach via IBM Cloud Code Engine, enabling scalable and efficient deployment without managing the underlying infrastructure. Each microservice exposes a public API endpoint to be consumed by the front-end application.

Following the successful deployment, the front-end application is accessed through its own deployment URL, demonstrating seamless communication and integration with the backend microservices.

This setup highlights the flexibility and scalability of serverless microservices and their ability to work together to power a dynamic, real-time product comparison platform.

## Deploying the Backend Microservices

#### 1. Deploy the microservice for Product Details, which provides API endpoints to retrieve product information.
```
build-context-dir - products_list
port - 5000
```
```bash
https://github.com/thanosdrome/dealer_evaluation_backend
```
```bash
ibmcloud ce application create --name prodlist --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist --registry-secret icr-secret --port 5000 --build-context-dir products_list --build-source https://github.com/thanosdrome/dealer_evaluation_backend
```


#### 2. Deploy the microservice for Dealer Pricing, which provides API endpoints to retrieve dealer pricing information.
```bash 
build-context-dir - dealer_details
port - 8080
```
```bash
https://github.com/thanosdrome/dealer_evaluation_backend
```
```bash
ibmcloud ce application create --name dealerdetails --imageus.icr.io/${SN_ICR_NAMESPACE}/dealerdetails --registry-secret icr-secret --port 8080 --build-context-dir dealer_details --build-source https://github.com/thanosdrome/dealer_evaluation_backend
```


#### You'll get a Deployment URL (Like in screenshots above), Copy and save it 

## Deploy the Frontend Microservice
Clone direct
```bash
https://github.com/thanosdrome/dealer_evaluation_frontend
```
#### Update the index.html file "produrl" and "dealerurl" with the deployment URLs obtained from the microservice deployments.

```build-context-dir - dealer_details
port - 5001
```

```bash
ibmcloud ce application create --name frontend --image us.icr.io/${SN_ICR_NAMESPACE}/frontend --registry-secret icr-secret --port 8080 --build-context-dir dealer_details --build-source .
```

## Your app Should be Live Like This
![product_all_dealers_prices](https://github.com/user-attachments/assets/378f7314-d71d-4f58-be31-2e87c84964ec)

## Author
#### Shudhanshu Ranjan
