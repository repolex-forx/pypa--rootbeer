# Repolex Knowledge Graph of pypa/rootbeer

RDF knowledge graph data for [pypa/rootbeer](https://github.com/pypa/rootbeer), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download pypa/rootbeer
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f121ac5e3b6e45bcdc1d4849ede9bf420bc8da2c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f121ac5e3b6e45bcdc1d4849ede9bf420bc8da2c
│           └── chunk-001.nq.gz
├── blob
│   ├── 0470d71b464cd8a6b6d5ff0c65dabc7253f87b6c.nq.gz
│   ├── 1a9c53588bf958814188ba9a6e13d50b924fdccd.nq.gz
│   ├── 1bb5a44356f00884a71ceeefd24ded6caaba2418.nq.gz
│   ├── 255e383a816ef58b74a7a858004195df7909277c.nq.gz
│   ├── 83f3763b54869a9e15032a4b48bc53f935a4b32e.nq.gz
│   ├── 853418f8521b64e7bbd0931caa4a2eefe140bcb2.nq.gz
│   ├── 89de354795ec7a7cdab07c091029653d3618540d.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── abc3b7833cdaf8b3a46774c6e6ae6505e0db1545.nq.gz
│   ├── b5ac1070294b478b7cc2ce677207ee08813bfa37.nq.gz
│   ├── cba8d8860740c8cc71720b2c8640c6b4d47ca4e2.nq.gz
│   ├── f0a9ee29fcaab6b5629443593d97d87060c0717f.nq.gz
│   ├── f4164cc6772ac9f7588596df4bdafb78bf7be82d.nq.gz
│   └── fb3adca5b73d54ead50a70b06e63e2c7a14d944a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f121ac5e3b6e45bcdc1d4849ede9bf420bc8da2c.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 20 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[pypa/rootbeer](https://github.com/pypa/rootbeer)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
