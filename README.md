# Llama Index Project

## Introduction
Llama Index is a Large Language Model (LLM) framework designed for efficient LLM application development, particularly in search and retrieval tasks. It indexes documents by breaking them into smaller nodes and creates embeddings with service context, storing them in a non-redundant manner. This framework enhances retrieval by using a query engine to find relevant documents and passing the prompt along with the retrieved context to the LLM for response generation. Llama Index is optimized for speed and efficiency in data lookup.

In this notebook, we will create a project using a Website URL as a data source and an embedding model to generate numerical embeddings stored in a vector store, utilizing a persist directory to avoid redundant storage. We will also define a retriever and an LLM to generate responses using the context from the query engine.

[Link](https://docs.llamaindex.ai/en/stable/) to the Llama Index documentation.

## Installation
Install the required packages using the following command:
```bash
!pip -q install llama-index langchain llama-index-readers-web llama-index-embeddings-langchain llama-index-llms-huggingface langchain-community
```

## Access Token
To use the HuggingFace Hub API, you need to provide your personal access token:
1. Visit [HuggingFace Hub](https://huggingface.co/settings/tokens) to get your personal access token.
2. If you do not have an account, create one by signing up.
3. Click the "New Token" button to create a new token.
4. Copy the token and paste it after running the following code block:
```python
import os
from getpass import getpass
HF_TOKEN = getpass()
os.environ['HUGGINGFACEHUB_API_TOKEN'] = HF_TOKEN
```

## Importing Required Packages
- Vector Store Index
- Simple Directory Reader
- Simple Web Page Reader
- Service Context
- Storage Context
- Node Parsers
- Sentence Splitters
- Huggingface Embeddings
- Huggingface Inference API

## Storing Context
We define the LLM and embedding model, store the context using indexing, and retrieve the context from the storage context.

### Define the Persist Directory, LLM Model, and Embedding Model
- Persist Directory: The location on disk where the indexed data and metadata are stored to avoid the time and cost of re-indexing the data.
- LLM Model: Uses the query and the retrieved documents to generate a response.
- Embedding Model: Generates vector embeddings which are to be stored in a vector store.

### Using the Persist Directory
If the user uploads new data, a new directory is created. If the uploaded data already exists in the persistent directory, the indexes for that data are retrieved from the existing directory.

## Defining the Query Engine
The query engine uses the index to retrieve relevant documents based on the query.

## Generating Responses
- Define the response synthesizer using the service context.
- Use the vector retriever and response synthesizer in the query engine to generate responses.


## Conclusion
This project demonstrates how to use the Llama Index framework for efficient LLM application development, focusing on indexing, retrieval, and response generation using a persist directory to manage storage efficiently. The HuggingFace Hub API is utilized for embedding and inference models.
