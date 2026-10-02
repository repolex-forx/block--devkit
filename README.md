# Repolex Knowledge Graph of block/devkit

RDF knowledge graph data for [block/devkit](https://github.com/block/devkit), parsed by [repolex](https://repolex.ai).

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
rlex download block/devkit
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b3e02e9a8b89f8bcae9f22ce4c466b1827b29804
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── b3e02e9a8b89f8bcae9f22ce4c466b1827b29804.nq.gz
│   └── repolex
│       └── b3e02e9a8b89f8bcae9f22ce4c466b1827b29804
│           └── chunk-001.nq.gz
├── blob
│   ├── 02a47acb7958ac5b339c193bc25f8c0bcbc82221.nq.gz
│   ├── 02cb8fcb5372748d4273b6a49eceb78fbdb15ce6.nq.gz
│   ├── 0367d2331a2cbfb3dadb43da08affe106a235c28.nq.gz
│   ├── 1dc9a8cbb1d50b96940e03fd10df302b02e3b858.nq.gz
│   ├── 22ee9637e2c69ba28c5945e0d6532178bafcbc2f.nq.gz
│   ├── 2507900535e9d3fdfb5a3e199488cecc697d36e0.nq.gz
│   ├── 25813eef772696281c5086718371ff32be2ea9db.nq.gz
│   ├── 275379fb0e4fcf365c5246dc25d5615c53f7b9b1.nq.gz
│   ├── 2b93ac2ab121f0c026a06e9f260d3984d51d7096.nq.gz
│   ├── 2d4899d47a406c47469908d901ba4db2264ecdb4.nq.gz
│   ├── 31559b7d115e3c105b328cce9b9dcd9774025061.nq.gz
│   ├── 383f4511d444516caed0fd113ee8a2b640cd2290.nq.gz
│   ├── 39f3d9865a4cf09dbe4ccfb36097b890c53a3fac.nq.gz
│   ├── 44d2e9b0dd64a8f1f0b225e34ae81dc395559491.nq.gz
│   ├── 5a9507666fcfa804345e352d9cf4458f6bab62e4.nq.gz
│   ├── 69e96b8e33dbdd2f7131d876cd027d450be30f4e.nq.gz
│   ├── 6bccf43368fd7c96d9c659562a5142b8b8cb98a1.nq.gz
│   ├── 70c8e60e90e5ce51e4b857cb7584de646b00df44.nq.gz
│   ├── 75306517965a54731b94dca8bace640e856af115.nq.gz
│   ├── 816066f4755caecbea428ebfe33fecd477e0bb7e.nq.gz
│   ├── 862ee3c28647e7a58801a75236855c269c1448ae.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── 906ee94ca6891416a56b8a1df9e0bbcc0000429d.nq.gz
│   ├── a93412d16793407eafc9bb111103b0d4cd5ea77e.nq.gz
│   ├── ab43321481b51d9ccbef8863364bd61b0485fe30.nq.gz
│   ├── bbed1e55e826c712e3b84856e1c9d0764674bab5.nq.gz
│   ├── e3e838bbdfd17247f5137c18e9176a7b5a7505cd.nq.gz
│   ├── e889550ba4cbc92a720527042e5f6e7a303bfcbc.nq.gz
│   ├── ed8af44b09c8308653f4c7195d7f26bcb584f68f.nq.gz
│   ├── f159893f7379295e97a200d9b0d0441d32f32925.nq.gz
│   ├── f7f4ce3730df45aac701e45dd94f087178ec7e77.nq.gz
│   └── fe28214d3352b0ed40820a4999317694c8b1ef57.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── b3e02e9a8b89f8bcae9f22ce4c466b1827b29804.nq.gz
├── filetree
│   └── b3e02e9a8b89f8bcae9f22ce4c466b1827b29804.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

14 directories, 41 files
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

[block/devkit](https://github.com/block/devkit)

---
*Parsed on 2026-10-02 by [repolex](https://repolex.ai)*
