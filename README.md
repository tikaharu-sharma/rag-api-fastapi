# RAG API with FastAPI

A local retrieval-augmented generation (RAG) pipeline built to learn how retrieval, augmentation, and generation fit together in a real AI system, rather than just calling a hosted LLM API directly.

## What this does

This project answers questions grounded in a custom knowledge base (a personal profile document) instead of relying purely on a language model's training data. It follows the core RAG pattern:

1. **Ingestion** (`build_knowledge_base.py`) — reads a source document, splits it into chunks, generates embeddings, and stores them in a local vector database (ChromaDB).
2. **Retrieval** — given a question, the system searches the vector database for the most relevant chunks of the source document.
3. **Augmentation + Generation** (`main.py`) — the retrieved chunks are inserted into a prompt alongside the question, and a language model generates an answer grounded in that retrieved context rather than guessing from memory alone.
4. **API layer** — the pipeline is exposed as a FastAPI service, so the RAG logic runs behind a REST endpoint rather than as a standalone script.

## Why I built it

I wanted hands-on experience with the actual mechanics of RAG (chunking, embedding, vector search, and prompt augmentation) and with FastAPI as a way to serve an AI pipeline as a real API, rather than only reading about these concepts.

## Tech used

- **FastAPI** — REST API layer
- **ChromaDB** — local vector database for storing and retrieving embeddings
- **Python** — pipeline and ingestion scripts
- Local model runtime (Ollama) for generation

## Status

This is a learning project built to understand RAG fundamentals end-to-end. It's not set up for others to run out of the box, since the sample knowledge base used here (`profile.txt`) is personal.