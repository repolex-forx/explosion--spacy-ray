# Repolex Knowledge Graph of explosion/spacy-ray

RDF knowledge graph data for [explosion/spacy-ray](https://github.com/explosion/spacy-ray), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/spacy-ray
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 09ffba5baa6ff0f694e05c0de17905ec6132c893
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 09ffba5baa6ff0f694e05c0de17905ec6132c893
│           └── chunk-001.nq.gz
├── blob
│   ├── 0d98a2b50c6b7be9ce7c1114aee083d2925ecfac.nq.gz
│   ├── 1a4f15b9c743b488f675111d2c2a6c0947528280.nq.gz
│   ├── 2c56f593eb7e822d49bf30a9937b6cc91d319737.nq.gz
│   ├── 5213667c3f6eabb0b1148a00c191dc10ca0fbcc5.nq.gz
│   ├── 550d95cfeed3db390b3f0e56b9bcf40627ea882c.nq.gz
│   ├── 5db40b6a8515d00da3aa133852decbf889f24863.nq.gz
│   ├── 6c0dde0c7ab80283471c51d203336c9875f821b7.nq.gz
│   ├── 706dafa9838ce3027d174650f03aa68024baa866.nq.gz
│   ├── 82b90fe378028357c75e4f8e6248bb69eb89fb37.nq.gz
│   ├── 87c9bdddd5b2ad5989ad55e2cf8ad82e804c5592.nq.gz
│   ├── 98d2df927eb3b48d799596ccd545712450682fab.nq.gz
│   ├── 9ec1382a414cf04e7744ae8b834895af348c388d.nq.gz
│   ├── b56aa10d6e3cb59a83bae10afe48169273ca8195.nq.gz
│   ├── bca6b49581982d51c0b2d7746dac329b5ebed57c.nq.gz
│   ├── c1a7121c1bd6c9648bc686c95b1c7a94dd69cdd3.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e730561ad2b2697235fa3ffa693146d931bb30b6.nq.gz
│   ├── e99099ab49068506800924fbdd4ec7b6c6478f3a.nq.gz
│   └── fc4b3b566814904e96b58601d63db1dcf4b61034.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 09ffba5baa6ff0f694e05c0de17905ec6132c893.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 27 files
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

[explosion/spacy-ray](https://github.com/explosion/spacy-ray)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
