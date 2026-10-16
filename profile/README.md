<a href="https://github.com/starlinghq/starling">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/starlinghq/.github/main/profile/banner-dark.svg">
    <img alt="Starling: real AI models, native to .NET. Verified against the reference." src="https://raw.githubusercontent.com/starlinghq/.github/main/profile/banner-light.svg" width="100%">
  </picture>
</a>

<p align="center">
  <a href="https://github.com/starlinghq/starling"><b>Starling</b></a> ·
  <a href="https://github.com/starlinghq/tokenizers"><b>Tokenizers</b></a> ·
  <a href="https://www.nuget.org/packages?q=Starlings"><b>NuGet</b></a> ·
  <a href="https://github.com/starlinghq/starling/blob/main/llms.txt"><b>llms.txt</b></a> ·
  <a href="https://github.com/starlinghq/starling/labels/good%20first%20issue"><b>Good first issues</b></a>
</p>

<p align="center">
  <a href="https://www.nuget.org/packages?q=Starlings.Models"><img alt="Starlings.Models on NuGet" src="https://img.shields.io/nuget/vpre/Starlings.Models.E5.Extensions.AI?label=Starlings.Models&color=22a884"></a>
  <a href="https://www.nuget.org/packages/Starlings.Tokenizers"><img alt="Starlings.Tokenizers on NuGet" src="https://img.shields.io/nuget/vpre/Starlings.Tokenizers?label=Starlings.Tokenizers&color=22a884"></a>
  <img alt=".NET 10" src="https://img.shields.io/badge/.NET-10-512BD4">
  <img alt="License: MIT OR Apache-2.0" src="https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue">
</p>

---

### Open models as ordinary NuGet packages

**Starling** runs real AI models inside your .NET app. You get embeddings, entity extraction, image and video search, and chat, with no Python sidecar and no cloud API. Each model is pinned to an exact upstream commit, verified by SHA-256, and checked against the original PyTorch/Python implementation before release. The evidence is published next to the code.

```csharp
using var embedder = E5EmbeddingGenerator.Create(await E5ModelAssets.DownloadAsync());
var vector = await embedder.GenerateVectorAsync("query: Which river runs through Cologne?");
// In-process on ONNX Runtime, CPU or CUDA. After the one-time download, no network.
```

<table>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/starlinghq/starling">starling</a></h3>
      <p>Local AI models for .NET on ONNX Runtime (CPU/CUDA), exposed through <code>Microsoft.Extensions.AI</code>: <code>IEmbeddingGenerator</code> and <code>IChatClient</code>. If your code already talks to a hosted provider, switching to a local model is a one-line change.</p>
      <pre lang="sh">dotnet add package Starlings.Models.E5.Extensions.AI --prerelease</pre>
      <p><a href="https://github.com/starlinghq/starling#quickstart">Quickstart →</a></p>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/starlinghq/tokenizers">tokenizers</a></h3>
      <p>Hugging Face <code>tokenizer.json</code> in pure .NET. Token ids, offsets and decoded text match <code>huggingface/tokenizers</code> case by case. No native code, no dependencies, and it fails loudly on anything it doesn't implement.</p>
      <pre lang="sh">dotnet add package Starlings.Tokenizers --prerelease</pre>
      <p><a href="https://github.com/starlinghq/tokenizers#supported-tokenizers">Supported tokenizers →</a></p>
    </td>
  </tr>
</table>

### Models

| | Model | What it does | Package |
| :-: | --- | --- | --- |
| 🔎 | [multilingual-e5-small](https://huggingface.co/intfloat/multilingual-e5-small) | Text embeddings in 100 languages | `Starlings.Models.E5` |
| 🖼️ | [EmbeddingGemma 2](https://huggingface.co/google/embeddinggemma-2) | Text, image and video embeddings in one space | `Starlings.Models.EmbeddingGemma2` |
| 🏷️ | [GLiNER2](https://huggingface.co/fastino/gliner2-base-v1) | Zero-shot entity extraction with any labels | `Starlings.Models.Gliner2` |
| 💬 | [Qwen3.5-0.8B](https://huggingface.co/Qwen/Qwen3.5-0.8B) | Chat and text generation via `IChatClient` | `Starlings.Models.Qwen35` |

The [model catalog](https://github.com/starlinghq/starling/blob/main/docs/catalog/README.md) links every release gate to its evidence: provenance, numerical parity, task quality, leak soak, benchmarks and clean install.

### What we care about

<table>
  <tr>
    <td width="25%" valign="top"><b>🎯 Faithful</b><br>The Python reference is what we test <i>against</i>. Parity is measured and published, not assumed.</td>
    <td width="25%" valign="top"><b>🏠 Local</b><br>Inference runs in-process. Your data stays on your machine, and the model can't change underneath you.</td>
    <td width="25%" valign="top"><b>🔓 No lock-in</b><br>Built only on vendor-neutral <code>Microsoft.Extensions.AI.Abstractions</code>. CI rejects Azure and OpenAI SDK dependencies.</td>
    <td width="25%" valign="top"><b>🧾 Explicit</b><br>Unsupported is an error, not an approximation. Each release gate links to its evidence.</td>
  </tr>
</table>

### Built for coding agents too

Every repo ships an [`llms.txt`](https://github.com/starlinghq/starling/blob/main/llms.txt). Starling also includes an [Agent Skill](https://github.com/starlinghq/starling/blob/main/skills/starling-dotnet/SKILL.md) that teaches Claude Code, Copilot, Cursor or Codex to use the packages correctly. To try it, paste this into your agent:

```text
Read https://raw.githubusercontent.com/starlinghq/starling/main/llms.txt and
https://raw.githubusercontent.com/starlinghq/starling/main/skills/starling-dotnet/SKILL.md,
then use the Starlings.* NuGet packages to <what you want to build>.
```

### Get involved

- ⭐ Star [starling](https://github.com/starlinghq/starling) and [tokenizers](https://github.com/starlinghq/tokenizers) to follow along
- 🐣 Pick up a [good first issue](https://github.com/starlinghq/starling/labels/good%20first%20issue)
- 🧪 [Request a model](https://github.com/starlinghq/starling/issues/new/choose) or [a tokenizer](https://github.com/starlinghq/tokenizers/issues/new?template=tokenizer-request.yml)
- 🤖 Add a model with your agent using the [starling-add-model skill](https://github.com/starlinghq/starling/blob/main/skills/starling-add-model/SKILL.md)

<sub>Everything here is in preview. Packages are published as prereleases on nuget.org, and APIs may change between minor versions. Code is dual-licensed MIT OR Apache-2.0. Model weights keep their own terms.</sub>
