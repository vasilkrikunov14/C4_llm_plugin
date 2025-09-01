# 🛠️ Architecture and Local Code Retrieval

> 🔐 *An on-premise, privacy-preserving architecture for context-aware LLM-powered code assistance.*

---

## 📦 System Overview
Our system comprises:

* 🌐 IDE plugin (JetBrains / VSCode)
* 🧠 On-premise LLM backend
* 🔍 Local Personal CodeRAG module
* 🩵 Logging & audit service

All code stays local. Only minimal metadata is shared.

### 🔹 Context-Level Architecture (C4)

![Context Level Diagram](../figures/Context_lvl.pdf)

> Developers interact with the plugin, which securely interfaces with internal LLMs and retrieval modules.

---

### 🔹 Container-Level Architecture (C4)

![Container Level Diagram](../figures/Container_lvl.pdf)

> Each container is modular and easily swappable: VSCode/JetBrains plugin, Admin UI, Ollama-based LLM backend, logging DB, and more.

---

## 🔍 Personal CodeRAG: Local Retrieval Engine

This client-side component ensures:

* **Full code privacy**
* **Fast semantic retrieval**
* **Rich context for LLM prompting**

### 🧠 Embedding Pipeline

* `BERT (fine-tuned)` — encodes both queries and code snippets
* `FAISS` — performs similarity search using embeddings
* `GGUF` — compresses the model under 2GB
* `Ollama` — lightweight inference server

### ⚙️ Local Workflow

```
1. Developer writes a prompt in IDE
2. CodeRAG embeds the query and searches local indexed code
3. Top-K relevant snippets are returned
4. Context is passed to LLM (on-prem/cloud-hosted) for generation
```

### ✨ Key Benefits

* 🔒 No code leaves the developer’s machine
* 🧹 Plug-and-play for different IDEs or LLM backends
* 💻 Works on low-resource environments (<2GB RAM)
* ⚙️ Fully modular and extensible

---

## ⚙️ Technologies Used

| Component          | Tool/Framework           |
| ------------------ | ------------------------ |
| IDE Plugin         | JetBrains / VSCode       |
| Retrieval Index    | FAISS                    |
| Embeddings         | BERT (Code-tuned)        |
| Model format       | GGUF                     |
| Orchestration      | Ollama                   |
| Hosting (optional) | Docker, Kubernetes, etc. |

---

## 🧠 Learn More

* [C4 Model](https://c4model.com/)
* [GGUF Format](https://github.com/ggerganov/ggml)
* [Ollama](https://ollama.com/)
* [FAISS](https://github.com/facebookresearch/faiss)

