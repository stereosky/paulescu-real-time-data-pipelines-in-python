<!-- <div align="center">
    <a href='https://www.realworldml.xyz/'><img src='./media/rwml_logo.png' width='350'></a>    
</div> -->

<div align="center">
    <h1>Build and deploy a production-ready real-time feature pipeline in Python</h1>
    <h2>Kafka + Python = <a href="https://github.com/quixio/quix-streams">Quix Streams</a> 🚀</h2>
    
</div>

#### Table of contents
* [The problem](#the-problem)
* [Example](#example)
* [How to run the pipeline locally](#run-the-pipeline-locally)
* [Deployment](#run-the-pipeline-locally)
* [Video lecture](#video-lecture)
* [Wanna learn more real-time ML?](#wanna-learn-more-real-time-ml)


## The problem

Imagine you want to build a trading bot for crypto currencies using ML.

Before you even get to work on your ML model, you need to design, develop and deploy a **real-time feature pipeline** that produces the features your model needs both at training time and at inference time.

This pipeline needs to

- **Ingest** raw data from an external service, like raw trades from the Kraken Websocket API.

- **Transform** these trades into features for your ML model, like trading indicators based on 1-minute OHLC candles, and

- **Save** these features in a Feature Store, so your ML models can fetch them both to generate training data, and to generate real-time predictions.

In a real-world setting, each of these steps is implemented as a separate service, and communication between these services happens through a message broker like Kafka.

[IMAGE]

This way you make your system scalable, by spinning up more containers as needed, and leveraging Kafka consumer groups.

And this is all great, but the question now is
> How do you implement this in practice?

Let's go through an example.

## Example

In this repo you have a full implementation of a production-ready real-time feature pipeline for crypto trading.

We use [Quix Streams 2.0](https://github.com/quixio/quix-streams) which is a cloud native library for processing data in Kafka using pure Python.

With Quix Streams we get the best from both worlds:

- low-level scalability and resiliency from Apache Kafka, so our code is production-ready from day 1, and

- an easy-to-use Python interface, which makes this library extremely user-friendly for Data Scientist and ML engineers like you and me.


## Run the pipeline locally in 5 minutes

1. Create an `.env` file and fill in the credentials to connect to the serverles Hopsworks Feature Store
    ```
    $ cp .env.example .env
    ```

2. Build Docker image for each of the pipeline steps: `trade_producer`, `trade_to_ohlc` and `ohlc_to_feature_store`
    ```
    $ make build
    ```

3. Start the pipeline
    ```
    $ make start
    ```

3. Stop the pipeline locally
    ```
    $ make stop
    ```

## Run the pipeline in production

This pipeline can run on any production environment that supports Docker and a message broker like Apache Kafka.

So, if you already have a Kubernetes cluster for your microservices, and use a Kafka broker

In this case, we will deploy it the pipeline to the Quix Cloud, ‍which provides fully managed containers, Kafka and observability tools to run your applications in production.




## Video lecture



## Wanna learn more real-time ML?

Join more than 10k subscribers to the Real-World ML Newsletter. Every Saturday morning.

[👉🏽 Click to subscribe](https://www.realworldml.xyz/subscribe)