<div align="center">

# 🐍 Python Graph Traversal

**A 1,000-file synthetic Python corpus of graph traversal implementations,
built to train and evaluate code language models.**

![Files](https://img.shields.io/badge/Files-1%2C000-2563eb?style=for-the-badge)
![Lines](https://img.shields.io/badge/Lines-1,739,445-16a34a?style=for-the-badge)
![Size](https://img.shields.io/badge/Size-48_MB-7c3aed?style=for-the-badge)
![Algorithms](https://img.shields.io/badge/Algorithms-3-db2777?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

---

> **Synthetic dataset.** Every module is machine-generated from a template bank of
> algorithm implementations. It is training data for a custom code model, not
> production library code.

## Overview

This repository is one of a ten-part thematic corpus. It contains **1,000 standalone
Python modules** covering graph traversal algorithms: breadth_first, depth_first, topological_sort.

Each file ranges from **100 to 4,000 lines**; every module compiles and every symbol
is namespaced with a file/block suffix so the whole corpus can be imported together.

## At a glance

| Property | Value |
| :-- | --: |
| Files (`.py`) | **1,000** |
| Total lines | **1,739,445** |
| Total size | **48.2 MiB** |
| Lines per file | **100 – 4,000** |
| Algorithms | **3** |
| Compile pass rate | **1,000 / 1,000** |
| Encoding / newlines | **UTF-8 / LF** |

## Algorithms

| Symbol | Algorithm | Average time | Variants |
| :-- | :-- | :-- | --: |
| `breadth_first` | Breadth-First Search | `O(V + E)` | 40,973 |
| `depth_first` | Depth-First Search | `O(V + E)` | 40,958 |
| `topological_sort` | Topological Sort | `O(V + E)` | 40,938 |

## File layout

```
algorithms/algorithm-XXXX.py
├── imports            # heapq, math, bisect, collections
├── ALGORITHM BLOCKS   # shuffled definitions, suffixed _XXXX_YYYY
├── LOOKUP_XXXX_NNN    # module constants for the exact line count
```

**Naming convention:** `{algorithm}_{file_index}_{block_index}` — for example,
`breadth_first_0042_0001`. The suffix makes every symbol in the corpus unique.

## Sample

Excerpt from `algorithms/algorithm-0042.py`:

```python
def breadth_first_0042_0001(graph, start):
    visited = {start}
    order = []
    queue = deque([start])
    while queue:
        node = queue.popleft()
        order.append(node)
        for neighbor in graph.get(node, []):
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return order
```

## Quality gates

- ✅ **Compiles cleanly** — every module passed `compile(source, path, "exec")`.
- ✅ **Exact line budget** — each file hits its 100–4,000 line target to the line.
- ✅ **Pure code** — no comments, no docstrings, no prose.
- ✅ **Deterministic** — a per-file seeded RNG reproduces the corpus.
- ✅ **Collision-free symbols** — all definitions carry a unique suffix.

## Intended use

Fine-tuning and pretraining code models; synthetic-data, tokenizer, retrieval, and
version-control experiments. Not suitable as production code or as a benchmark of
human-written style.

## License

No license has been specified yet. Until one is added, treat the content as all
rights reserved by the repository owner.
