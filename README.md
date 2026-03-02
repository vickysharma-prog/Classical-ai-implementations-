<div align="center">

# 🧠 Classical AI Implementations

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Pygame](https://img.shields.io/badge/Pygame-2.0+-00D000?style=flat-square&logo=python&logoColor=white)](https://pygame.org)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)

**Production-ready implementations of classical AI algorithms**

[Search](#1-bfs-actor-connections) • [Game Theory](#2-minimax-tic-tac-toe) • [Upcoming](#-upcoming-projects) • [Quick Start](#-quick-start)

</div>

---

## 🎯 About

Production-quality implementations of fundamental AI algorithms with clean, well-documented code covering
**Search**, **Game Theory**, **Knowledge Representation**, and **Probabilistic Reasoning**.

| Feature | Description |
|:--------|:------------|
| 📚 **Educational** | Detailed explanations with algorithm visualizations |
| 🏗️ **Well-Structured** | Clean architecture following best practices |
| 📖 **Documented** | Comprehensive documentation for each algorithm |
| 🧪 **Tested** | Verified implementations with sample datasets |

---

## 🚀 Projects

### 1. BFS Actor Connections
> **Six Degrees of Separation** — Find shortest path between any two actors through shared movies.

**📍 Location:** `search-algorithms/bfs-actor-connections/`

| Metric | Value |
|:-------|:------|
| Algorithm | Breadth-First Search |
| Time Complexity | O(V + E) |
| Space Complexity | O(V) |
| Optimality | ✅ Guaranteed shortest path |

#### How It Works
Tom Hanks → Kevin Bacon

Step 1: Start from Tom Hanks
Step 2: Explore all co-actors (level by level)
Step 3: Find Kevin Bacon
Step 4: Backtrack to get path

Result: Tom Hanks ─[Apollo 13]─→ Kevin Bacon (1 degree)


#### Algorithm

```python
def shortest_path(source, target):
    frontier = QueueFrontier()
    frontier.add(Node(state=source, parent=None, action=None))
    explored = set()

    while not frontier.empty():
        node = frontier.remove()

        if node.state == target:
            return reconstruct_path(node)

        explored.add(node.state)

        for movie_id, actor_id in neighbors_for_person(node.state):
            if actor_id not in explored and not frontier.contains_state(actor_id):
                child = Node(state=actor_id, parent=node, action=movie_id)
                frontier.add(child)

    return None
```
**Run**
```Bash

cd search-algorithms/bfs-actor-connections
python degrees.py data/large
```
**Output**
```text

Loading data...
Data loaded.
Name: Emma Watson
Name: Tom Hanks
3 degrees of separation.
1: Emma Watson and Brendan Gleeson starred in Harry Potter and the Goblet of Fire
2: Brendan Gleeson and Tom Hanks starred in The Green Mile
```
**2. Minimax Tic-Tac-Toe**
Unbeatable AI — Optimal game-playing agent using Minimax algorithm.

📍 Location: adversarial-search/minimax-tictactoe/

Metric	Value
Algorithm	Minimax
Time Complexity	O(b^d) ≈ O(9!)
Space Complexity	O(d) = O(9)
Optimality	✅ Perfect play (never loses)
**How Minimax Works**
```text

         Current Board (X's turn)
                  │
    ┌─────────────┼─────────────┐
    ▼             ▼             ▼
 Move A        Move B        Move C
 Score:+1      Score:0       Score:+1
 (X wins)      (Draw)        (X wins)
    │             │             │
    └─────────────┴─────────────┘
                  │
          MAX chooses +1
           (Best move)
```
**Features**
Feature	Description
🎮 Play as X or O	Choose your side
🤖 AI Never Loses	Optimal play guaranteed
🖥️ Visual Interface	Clean Pygame GUI
🏗️ Architecture
```text

Classical-ai-implementations/
├── search-algorithms/
│   └── bfs-actor-connections/
│       ├── degrees.py              # BFS implementation
│       ├── util.py                 # Node, Frontier classes
│       └── data/
│           ├── small/              # Test dataset
│           └── large/              # Full IMDb dataset
│
├── adversarial-search/
│   └── minimax-tictactoe/
│       ├── tictactoe.py            # Game logic + Minimax
│       └── runner.py               # Pygame GUI
│
├── README.md
├── LICENSE
└── requirements.txt
```

---

## 🔬 Algorithms Comparison

### Search Algorithms

| Algorithm | Complete | Optimal | Time | Space |
|:----------|:--------:|:-------:|:----:|:-----:|
| BFS | ✅ | ✅ | O(b^d) | O(b^d) |
| DFS | ❌ | ❌ | O(b^m) | O(bm) |
| A* | ✅ | ✅ | O(b^d) | O(b^d) |

### Game Theory

| Algorithm | Description | Pruning |
|:----------|:------------|:-------:|
| Minimax | Full game tree search | ❌ |
| Alpha-Beta | Minimax with pruning | ✅ |
| Expectimax | Handles randomness | ❌ |

---

## 🔮 Upcoming Projects

| Project | Algorithm | Category | Status |
|:--------|:----------|:---------|:------:|
| Minesweeper | Propositional Logic | Knowledge-based | 🔄 In Progress |
| PageRank | Markov Chains | Probabilistic | 📅 Planned |
| Heredity | Bayesian Networks | Probabilistic | 📅 Planned |
| Crossword | CSP + AC-3 | Constraint-based | 📅 Planned |
| Parser | Context-Free Grammar | NLP | 📅 Planned |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|:-----------|:--------|
| Python 3.10+ | Core language |
| Pygame | Game visualization |
| Git | Version control |

**Concepts:** Graph Theory, Game Trees, State Space Search, Adversarial Search, Heuristics

---

**⚡ Quick Start**
```Bash

# Clone
git clone https://github.com/vickysharma-prog/Classical-ai-implementations-.git
cd Classical-ai-implementations-

# Install dependencies
pip install pygame

# Run BFS project
cd search-algorithms/bfs-actor-connections
python degrees.py data/small

# Run Minimax project
cd ../../adversarial-search/minimax-tictactoe
python runner.py
```

**🤝 Contributing**
Fork the repository
Create feature branch (git checkout -b feature/amazing-feature)
Commit changes (git commit -m 'Add amazing feature')
Push to branch (git push origin feature/amazing-feature)
Open Pull Request
Ideas: Alpha-Beta pruning, A* search, Unit tests, Interactive visualizations

**📚 References**
Russell & Norvig — Artificial Intelligence: A Modern Approach (4th Ed.)
Harvard CS50 AI

📄 License
MIT License — see LICENSE for details.

<div align="center">
Made with ❤️ by Vicky Sharma

⭐ Star this repo if you found it helpful!

</div> ```
