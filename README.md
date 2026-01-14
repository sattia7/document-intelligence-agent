# Document Intelligence Agent (Offline RAG System)

## Overview

This project implements a **fully offline, production-ready Document Intelligence Agent** based on **Retrieval-Augmented Generation (RAG)** principles.  
The system allows users to upload PDF documents, index their contents locally, and interact with them in a **chat-style question-answering interface** — without relying on external APIs or cloud services.

The application is designed for **technical, engineering, and domain-specific document analysis**, where data privacy, reproducibility, and explainability are critical.

---

## Key Objectives

- Enable **offline document understanding** using local embeddings and LLMs
- Provide **chat-style Q&A** over user-uploaded PDFs
- Preserve **traceability** by showing document sources for each answer
- Support **incremental indexing** and efficient retrieval
- Deliver a **clean Streamlit UI** suitable for professional workflows
- Make the system **replicable and extensible** by other engineers

---

## System Architecture

The system follows a modular RAG architecture:


---

## Technology Stack

### Core Components

- **Python 3.10+**
- **Streamlit** – Interactive UI
- **LangChain** – Document handling and RAG orchestration
- **FAISS** – High-performance local vector search
- **SentenceTransformers** – Local text embeddings
- **PyPDF2 / PDF Loader** – PDF parsing
- **Local LLM (Offline)** – Answer generation
- **Pickle / Disk Caching** – Index persistence

---

## Functional Workflow

### 1. Document Ingestion
- Users upload one or more PDF files
- Each document is parsed and converted into raw text
- Metadata (file name, page number) is preserved

### 2. Intelligent Text Chunking
- Text is split using a recursive chunking strategy
- Chunk size and overlap are optimized for semantic coherence
- Prevents context loss while maximizing retrieval accuracy

### 3. Embedding Generation
- Each text chunk is converted into a dense vector using
  **SentenceTransformer embeddings**
- Embeddings are computed **once** and cached locally

### 4. Vector Indexing (FAISS)
- All embeddings are stored in a FAISS index on disk
- Enables fast similarity search even for large document sets
- Index can be reused across sessions

### 5. Chat-Style Question Answering
- User submits a question via the UI
- The system retrieves the top-K most relevant chunks
- Retrieved content is injected into a controlled prompt
- The LLM generates an answer **strictly grounded in context**

### 6. Explainability & Traceability
- Each answer includes:
  - Clear formatting
  - Source document references
- Prevents hallucination and improves trust

---

## User Interface Design

- Persistent **Q&A chat history**
- Questions remain visible with numbered answers
- “Thinking…” placeholders improve perceived responsiveness
- Sources displayed per answer
- Index build status clearly communicated
- Clean, professional UI suitable for technical users

---

## Offline-First Design Philosophy

This project was intentionally designed to:

- Avoid cloud dependencies
- Protect sensitive documents
- Enable use in restricted environments (rig sites, labs, secure networks)
- Maintain full control over models and data

---

## Project Structure

Document-Intelligence-Agent/
│
├── app.py # Main Streamlit application
├── embeddings/ # Local FAISS index & metadata
├── data/
│ └── pdfs/ # Uploaded documents
├── utils/
│ ├── loaders.py # PDF loading logic
│ ├── indexing.py # Chunking & indexing
│ └── qa.py # Retrieval & prompting
├── notebooks/
│ └── experiments.ipynb # Development & testing notebook
├── .gitignore # Excludes main code & sensitive files
├── requirements.txt
└── README.md

## 🔒 Code Policy
Main application code and notebooks are intentionally excluded.

This repository contains:
- Project structure
- Documentation
- Templates

Contact the author for access to the full implementation.
