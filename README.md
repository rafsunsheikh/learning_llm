# Document-Driven Chat Application with Streamlit and LlamaCPP

Welcome to the Document-Driven Chat Application repository! This project demonstrates how to create an interactive chat application that leverages the power of AI and machine learning to provide insights and interactions based on uploaded documents. The application is built using Streamlit, LlamaCPP, and FAISS.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [How It Works](#how-it-works)
- [Contributing](#contributing)
- [License](#license)

## Introduction

In the rapidly evolving world of AI and machine learning, integrating advanced models with user-friendly applications is becoming increasingly important. This repository provides a guide to building a document-driven chat application using Streamlit and LlamaCPP. The application allows users to upload text documents and interact with them through a chat interface powered by LlamaCPP embeddings and the Qwen-0.5B-Chat model.

## Features

- **Document Upload:** Upload text documents (`.txt` or `.md`) for analysis.
- **Chat Interface:** Interact with the document through a chat interface.
- **AI-Powered Responses:** Utilize the Qwen-0.5B-Chat model for intelligent responses.
- **Document Embeddings:** Generate embeddings for documents using LlamaCPP.
- **Efficient Retrieval:** Use FAISS for efficient document retrieval during chat interactions.

## Installation

### Prerequisites

- Python 3.7+
- Streamlit
- pip

### Install Dependencies

To install the necessary dependencies, run:

```bash
pip install streamlit rich tiktoken langchain llama-cpp faiss-cpu
```

## Usage

### Running the Application

1. Clone the repository:

```bash
git clone https://github.com/yourusername/document-driven-chat.git
cd document-driven-chat
```

2. Run the Streamlit application:

```bash
streamlit run app.py
```

3. Open your web browser and go to `http://localhost:8501` to access the application.

## Configuration

### Embeddings and Chat Model

Ensure you have the necessary model files and update the paths in the `create_embeddings` and `create_chat` functions:

```python
@st.cache_resource 
def create_embeddings():   
    embpath = "/path/to/all-MiniLM-L6-v2.F16.gguf"
    embeddings = LlamaCppEmbeddings(model_path=embpath)
    return embeddings

@st.cache_resource 
def create_chat():   
    qwen05b = Llama(
                model_path='/path/to/qwen2-0_5b-instruct-q8_0.gguf',
                n_gpu_layers=0,
                temperature=0.1,
                top_p=0.5,
                n_ctx=8192,
                max_tokens=600,
                repeat_penalty=1.7,
                stop=["", "Instruction:", "### Instruction:", "###<user>", "</user>"],
                verbose=False)
    return qwen05b
```

## How It Works

1. **Document Upload:** Users upload a text document which is read and split into chunks.
2. **Embeddings:** The chunks are converted into embeddings using LlamaCPP.
3. **Vector Store:** A FAISS vector store is created for efficient retrieval.
4. **Chat Interaction:** Users interact with the document through a chat interface. The chat model generates responses based on the document content.

## Contributing

Contributions are welcome! If you'd like to contribute, please fork the repository and create a pull request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

Feel free to customize the sections and content according to your project's specific details and requirements.
