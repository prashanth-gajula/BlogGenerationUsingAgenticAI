# Blog Generation Agent

This repository contains a **Blog Generation Agent** powered by **OpenAI's GPT-4o** and **LangChain**. The agent assists in generating blog content by leveraging LangChain's graph-based workflow and message handling capabilities.

## 📌 Features
- Uses OpenAI's **GPT-4o** model to generate blog content.
- Implements **LangChain** for structured interactions.
- Loads API keys securely from a **.env** file.
- Implements an **agent graph** for step-wise blog generation.

## 📂 Project Structure
```
├── Blog_Generation_Agent.ipynb  # Main Jupyter Notebook
├── .env                         # Environment variables (not included in repo)
├── README.md                    # Documentation
└── requirements.txt              # Required Python packages
```

## 🔧 Setup & Installation
1. **Clone the repository:**
   ```sh
   git clone https://github.com/yourusername/Blog_Generation_Agent.git
   cd Blog_Generation_Agent
   ```
2. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```
3. **Set up API key:**
   - Create a `.env` file in the root directory.
   - Add the following line:
     ```sh
     OPENAI_API_KEY=your_api_key_here
     ```

## 🛠️ Code Explanation
### 1️⃣ Loading API Key
```python
import os
from dotenv import load_dotenv
load_dotenv()
os.environ['OPENAI_API_KEY'] = os.getenv('OPENAI_API_KEY')
```
- Loads environment variables from `.env`.
- Retrieves `OPENAI_API_KEY` for authentication.

### 2️⃣ Initializing GPT-4o Model
```python
from langchain_openai import ChatOpenAI
model = ChatOpenAI(model="gpt-4o")
```
- Initializes OpenAI's GPT-4o model via **LangChain**.

### 3️⃣ Creating a Chat Agent
```python
from langchain_core.messages import HumanMessage, SystemMessage
result = model.invoke("Hello")
print(result.content)
```
- Sends a message to the GPT-4o model.
- Receives and prints the response.

### 4️⃣ Understanding LangGraph
**LangGraph** is a framework for creating structured, multi-step workflows using LangChain. It allows us to define an execution graph where different steps can be connected based on logic and conditions.

In this project, we use **LangGraph** to create an agent graph that guides the blog generation process step by step.

Example of a basic LangGraph workflow:
```python
from langgraph.graph import StateGraph

def step1(input_text):
    return f"Processing: {input_text}"

def step2(processed_text):
    return f"Final Output: {processed_text}"

# Define a graph with two steps
graph = StateGraph()
graph.add_node("step1", step1)
graph.add_node("step2", step2)
graph.add_edge("step1", "step2")
```
This approach allows us to structure complex workflows efficiently.

### 5️⃣ Setting Up an Agent Graph for Blog Generation
```python
from langgraph.graph.message import add_messages
from typing_extensions import TypedDict
from typing import Annotated
```
- Imports required components for building a structured agent.

## 📌 Example Usage
To run the blog generator, execute the notebook `Blog_Generation_Agent.ipynb`. Modify the prompts and agent logic as needed.

## 📷 Visual Representation
![LangChain Workflow](https://raw.githubusercontent.com/langchain-ai/langchain/main/docs/assets/langchain.svg)

## 📜 License
This project is licensed under the MIT License.

## 🤝 Contributions
Feel free to submit pull requests or open issues for feature requests and improvements.

---
🚀 **Happy Blogging!**


