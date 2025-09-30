# LangGraph

This repository contains a collection of **LangGraph examples** demonstrating how to build and execute different types of AI-powered graphs using [LangGraph](https://github.com/langchain-ai/langgraph).

LangGraph is a Python framework for building **graphs of LLM calls, computations, and stateful operations**.  
Each graph consists of **nodes** (units of computation or model interaction) connected by **edges** that define the flow of execution.  
This approach allows developers to build modular, reusable, and adaptive workflows for AI applications.

---

## 📂 Examples Overview

### 1. Sequential Graphs
Sequential graphs demonstrate step-by-step task flows where each node executes in order.

- **BMI Calculator Graph**  
  - **Inputs**: Weight and height  
  - **Process**: Calculates Body Mass Index (BMI)  
  - **Output**: BMI value + category (Underweight, Normal, Overweight, Obese)

- **State-based LLM Graph**  
  - **Inputs**: Initial state  
  - **Process**: Invokes LLM nodes that update the `final_state`  
  - **Output**: Updated state after execution  

- **Prompt Chaining Graph**  
  - **Step 1**: Generate outline from input  
  - **Step 2**: Use outline to create a blog post  
  - **Output**: Short blog article  

---

### 2. Parallel Graphs
Parallel graphs run multiple nodes independently and then merge results into a combined state.

- **Batsman Performance Graph**  
  - **Inputs**: Runs, balls faced, fours, sixes  
  - **Outputs** (in parallel): Strike rate, balls per boundary, boundary percentage, and performance summary  

- **UPSC Essay Evaluation Graph**  
  - **Inputs**: Essay text (initial state)  
  - **Parallel Evaluations**: Analysis, Language, Depth of Thought  
  - **Aggregation**: Combines evaluations → produces summary, score, and label (`Good`, `Poor`, or `Excellent`)  
  - **Output**: Updated `final_state` with evaluation results  

---

### 3. Conditional Graphs
Conditional graphs use branching logic, where execution depends on intermediate results.

- **Quadratic Equation Graph**  
  - **Inputs**: Coefficients `a`, `b`, `c`  
  - **Process**: Computes discriminant → determines number of solutions:  
    - `Discriminant < 0` → No real roots  
    - `Discriminant = 0` → One root  
    - `Discriminant > 0` → Two distinct roots  

- **Review Reply Graph**  
  - **Inputs**: Review text  
  - **Process**:  
    - Detects sentiment → Positive or Negative  
    - **If Positive**: Ends graph with a “Thank you” response  
    - **If Negative**: Runs a diagnosis subgraph → generates empathetic resolution → ends graph  
  - **Output**: Adaptive, context-sensitive reply  

---

### 4. Iterative Graphs
Iterative graphs support loops, where outputs are reprocessed until a stopping condition is met.

- **X Post (Tweet) Generator Graph**  
  - **Input**: Topic  
  - **Process**:  
    1. Generate funny tweet draft (LLM 1)  
    2. Evaluate tweet (`Approved` / `Needs Improvement`) (LLM 2)  
    3. If **Approved** → End graph  
    4. If **Needs Improvement** → Optimize tweet (LLM 3) → Re-evaluate → Repeat  
    5. Stop if approved or if **max iterations** reached → auto-approve last version  
  - **Output**: Approved tweet after loop completion  

---

### 5. Persistent
Persistent demonstrates **state management, recovery, and fault tolerance** in LangGraph.

- **Chatbot with InMemorySaver**  
  - Uses **InMemorySaver** to temporarily store chat history during execution  
  - Useful for experiments and short-term use cases  

- **Checkpointers**  
  - Save intermediate states of a graph to storage  
  - Enable resuming execution from the last checkpoint instead of restarting  

- **Time Travel**  
  - Inspect or revert to previous states in the graph  
  - Useful for debugging, auditing, and analysis  

- **Updating State**  
  - Nodes dynamically update the shared `state`  
  - Subsequent nodes always see the most recent values  

- **Fault Tolerance**  
  - Recovers from errors using checkpoints  
  - Ensures reliability for long-running or critical applications 
