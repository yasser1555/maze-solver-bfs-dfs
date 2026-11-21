<div align="center">

# Maze Solver — BFS & DFS (C++)

**Graph Algorithms · Data Structures · File I/O · Academic Team Project**

A command-line C++ application that loads a grid maze from a text file, solves it using **Breadth-First Search (BFS)** and **Depth-First Search (DFS)**, and writes the resulting paths to separate files.

[Developer portfolio](https://yasser-alassad-portfolio.vercel.app/) · [GitHub profile](https://github.com/yasser1555)

</div>

## Overview

The program compares two graph traversal approaches on the same unweighted grid:

- **BFS:** Uses a queue and parent tracking to find a shortest route in terms of grid moves when a route exists.
- **DFS:** Uses a stack and parent tracking to explore a route; its result is **not guaranteed** to be shortest.

The implementation is separated into input/output helpers (`maze.cpp`, `maze.h`), search algorithms (`solver.cpp`, `solver.h`), and a CLI entry point (`main.cpp`). The input is checked for rectangular rows, supported symbols, and exactly one start and one exit.

## Technologies

- C++17 (`std::filesystem` for the output directory)
- C++ Standard Library: `std::vector`, `std::queue`, `std::stack`, `std::ifstream`, `std::ofstream`
- Graph traversal, path reconstruction, and basic input validation

## Quick Start

**Prerequisite:** A C++17 compiler such as GCC (`g++`). No third-party libraries are needed.

From the repository root, compile:

```bash
g++ -std=c++17 -Wall -Wextra -pedantic main.cpp maze.cpp solver.cpp -o maze_solver
```

Run on macOS/Linux:

```bash
./maze_solver
```

Run on Windows (if compiled as `maze_solver.exe`):

```powershell
.\maze_solver.exe
```

When prompted, type:

```text
maze.txt
```

The application prints the original and solved mazes and writes `output/solved_bfs.txt` and `output/solved_dfs.txt`. The `output/` directory is created at runtime and is deliberately not version-controlled.

## Maze Format

`maze.txt` is a 6-row example. A maze must be rectangular and contain:

| Symbol | Meaning |
|---|---|
| `S` | Start (exactly one) |
| `E` | Exit (exactly one) |
| `0` | Walkable cell |
| `1` | Wall |

```text
S000100
1001010
1001010
1011010
1000000
100000E
```

Solved routes are indicated by `*` while `S` and `E` remain visible.

## Example Results

On the included `maze.txt`, the program compiled and ran successfully with `g++ -std=c++17` during packaging.

| Search | Printed "Path Steps" | Route type |
|---|---:|---|
| BFS | 10 | Shortest path in this unweighted grid |
| DFS | 12 | A valid path, not necessarily shortest |

**Note:** In this implementation, `countPathSteps()` counts the `*` characters **between** the `S` and `E` markers, not all edge moves. Consequently, the reported values are the number of marked intermediate cells; the corresponding routes in this example have 11 and 13 moves respectively.

### BFS output

```text
S*00100
1*01010
1*01010
1*11010
1******
100000E
```

### DFS output

```text
S*00100
1*01010
1*01010
1*11010
1*0***0
1***0*E
```

## Project Structure

```text
README.md
.gitignore
main.cpp
maze.cpp
maze.h
solver.cpp
solver.h
maze.txt
```

## Complexity

For a grid of `R` rows and `C` columns, both algorithms visit each reachable cell at most once and check up to four neighbors per cell, giving **O(R × C) time** and **O(R × C) auxiliary space** in the worst case (visited cells and parent data).

## Limitations

- CLI-only; there is no graphical interface.
- The maze is unweighted and traversal is limited to four cardinal directions.
- The program exits on invalid maze content instead of providing an interactive retry.
- The sample counts in the console exclude start and end markers, as noted above.

## Team Project & Attribution

This was developed as an **academic team project**. It is included as a team-work portfolio example; **individual coding contributions are not claimed here**. The source archive also identifies an [original team repository](https://github.com/DevxDex/MazeSolver). This showcase is not presented as solely authored by the portfolio owner.

**Portfolio:** [Yasser Alassad](https://yasser-alassad-portfolio.vercel.app/) · [LinkedIn](https://www.linkedin.com/in/yasser-alassad/)

> **Publishing note:** Source code can be published only with the relevant contributors' permission or another valid right to redistribute it. No open-source license is asserted in this repository.
