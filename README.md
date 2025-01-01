# rag-evaluation-with-mlflow
This repository contains sample code to evaluate RAG systems using Mlflow.
Overview

One of the most common architecture patterns used for leveraging generative AI is Retrieval Augmented Generation (RAG). Performance of RAG systems depends on several factors including chunking, embedding algorithms, vector databases, etc. This repository contains sample code for evaluating RAG systems using Mlflow metrics, relevance and toxicity. Please note that the code provided here is for illustrative purposes only and is not for production deployment. Refer to the below documentation  links for additional details on Mlflow services and metrics.

Services and libraries were issued to illustrate the solution.

•	Azure Open AI: gpt-4 is used for embedding and completions.
•	Open AI: Mlflow uses Open AI for evaluation
•	Chroma and Qdrant: Vector databases for storing embedded domain specific documents.
•	Mlflow AI Gateway(Experimental): A central configuration management service deployed locally. LLM provider, endpoint and API keys can be stored using Mlflow API gateway.
•	Mlflow Tracking server: MLflow tracking server is a stand-alone HTTP server that serves multiple REST API endpoints for tracking runs/experiments.
•	Langchain
•	Sample Mlflow documentation for QnA.




Prerequisites

1.	On a terminal window in your local device, run the below steps.
a.	Deploy local Mlflow AI Gateway (Experimental) on a local device using mlflow AI Gateway documentation and validate the server is running and accessible by accessing http://127.0.0.1:<port>, default port is 5000. Note, Mlflow AI Gateway server is not supported on Windows platform.
b.	 Start local Mlflow tracking server using Mlflow Start Mlflow tracking server
mlflow server --host 127.0.0.1 --port 8080 

2.	Create environmental variables, including the below

AZURE_OPENAI_API_KEY
OPENAI_API_KEY
AZURE_OPENAI_ENDPOINT

Prerequisites


Run the remaining steps in a  Jupyter Notebook. A sample notebook can be found in the repository.
1.	Install prerequisites using the requirements.txt file provided in the repository
2.	Run cells in the Jupyter notebook
a.	Import necessary libraries and packages, run the below import statements in a cell 
b.	Set and Retrieve required environment variables
c.	Load MLflow sample documents using Langchain’s WebBaseLoader, embed and ingest the loaded documents into Chroma and Qdrant vector databases
d.	Create a dataframe with sample questions and evaluate the RAG application with mlflow.evaluate
e.	Plot metrics accuracy, relevance and toxicity
3.	Experiment using different chunk_sizes, embedding LLMs and different vector databases and monitor performance using Mlplot and Mlflow tracking UI. The Jupyter notebook in this repository contains code to compare vector databases Chroma and Qdrant for demonstrating how Mlflow metrics and the evaluate function can be used to measure and compare latency and relevance of the Question-Answers application. 

4.	To access the tracking server, use this link http://127.0.0.1:<port>, default port is 8080 to view details of experiments visually.

Notes
•	MLflow AI Gateway is an experimental service, and this service may undergo changes continuously. Please refer to Mlflow documentation for additional details.
•	Selecting  Vector databases, embedding algorithms, chunking sizes, etc. depend on the use case. It requires lot of experimentation and testing to arrive at optimal configuration. 
•	The purpose of this illustration is to introduce beginners to the concepts of experimentation using  Mlflow AI Gateway, Mlflow tracking server and MLflow evaluate function. Any comparative analysis and graphs shown in this tutorial are purely for illustration only but not to indicate one component is better than the other.
. A note- this tutorial utilizes the sample notebook provided by MLflow documentation however, instead of leveraging LLM endpoints hosted on Databricks, I used a local MLflow AI gateway to configure endpoints for LLMs and leveraged the gateway’s APIs for accessing models for embeddings and completions![image](https://github.com/user-attachments/assets/780bba0b-fec7-4b17-9163-4357cee636ff)







References

1.	https://www.mlflow.org/docs/2.7.1/what-is-mlflow.html#:~:text=MLflow%20is%20a%20versatile%2C%20expandable,%2C%20algorithm%2C%20or%20deployment%20tool.
2.	https://mlflow.org/docs/latest/llms/deployments/index.html
3.	https://mlflow.org/docs/latest/tracking/server.html
4.	https://mlflow.org/docs/latest/llms/llm-evaluate/index.html

![image](https://github.com/user-attachments/assets/459aeb6c-db36-4dfb-b216-55a6a510ee7f)
