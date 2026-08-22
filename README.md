# DigitalOcean Gradient AI: The Complete Cloud GPU & LLM Inference Guide — From 1-Click Model Deployment to Building Production Agents, Plus Plan-by-Plan Pricing Breakdown (With $200 Free Credit)

If you've spent any real time in the AI space lately, you've probably run into the same wall everyone keeps hitting: hyperscaler GPU clouds are powerful, but they're also expensive, complicated, and somehow always out of stock when you need them most. There's a quieter option that a lot of developers and small teams have been quietly migrating to — **DigitalOcean Gradient AI**, the platform formerly known as Paperspace, now rebuilt into a full-stack AI cloud that bundles GPU compute, serverless inference, agent tooling, and managed data under one roof. This guide walks through what Gradient actually offers, how its pricing works across every tier, who it fits best, and how to get the $200 free credit that's been quietly funding a lot of startup experiments.

## What Is DigitalOcean Gradient AI, Really?

To understand Gradient, it helps to know where it came from. DigitalOcean acquired Paperspace back in 2023, and rather than just slapping a new logo on the old product, they rebuilt it. Gradient is now positioned as what DigitalOcean calls an "AI-Native Cloud" — meaning it's not just a place to rent GPUs, but a layered stack where you can go from raw GPU Droplets all the way up to managed agents that call OpenAI, Anthropic, and open-source models through a single inference endpoint.

The throughline is simplicity. Where AWS makes you piece together EC2, SageMaker, Bedrock, and a dozen other services, Gradient tries to keep everything under one console, one billing statement, and one API key system. That's the pitch, at least. Whether it actually delivers depends a lot on what you're building.

## The Core Layers of the Gradient Stack

**GPU Droplets — raw compute for training and inference**

This is the foundation. GPU Droplets are virtual machines backed by NVIDIA and AMD silicon, billed per-second with a 5-minute minimum, and pre-loaded with PyTorch, CUDA, and the usual deep-learning toolchain so you can start working the moment the instance boots. You can spin up a single GPU for a quick experiment or jump to 8-GPU configurations for serious model training.

**Serverless Inference — 70+ models on one endpoint**

This is where things get interesting. Instead of provisioning your own GPU and running vLLM manually, you can call a single DigitalOcean inference endpoint and route requests across more than 70 models — frontier options like Claude Sonnet 5, GPT-5.5, and GPT-5.6 Sol alongside open-weight models like DeepSeek V4 Pro, Qwen 3.5, GLM-5.2, and Llama 4 Maverick. Pricing mirrors the upstream provider's published rates, so there's no surprise markup. The Inference Router feature (currently in public preview, free during preview) lets you define policy-based routing in natural language — say, "use the cheapest model unless latency exceeds 2 seconds" — and the platform figures out the rest.

**1-Click Models — instant self-hosted LLMs**

If you'd rather run models on your own GPU Droplet instead of paying per-token, 1-Click Models let you deploy popular Hugging Face and DeepSeek models with a single click — zero configuration. It's the fastest path from "I want to try DeepSeek R1" to "I have DeepSeek R1 running on an H100 with a public API endpoint."

**Agent Platform — production agents without infrastructure**

The Agent Platform is the newest layer, and it's where Gradient genuinely diverges from most competitors. You build agents through UI templates or Python SDKs (the open-source Agent Development Kit, or ADK, lives on GitHub), connect them to knowledge bases, give them tools, and deploy them with their own API endpoints. Agent creation itself is free — you only pay for the underlying model tokens, knowledge base indexing, and any guardrails you enable.

**Knowledge Bases and Vector Databases — managed RAG infrastructure**

Gradient includes a fully managed RAG service that handles embedding, chunking, retrieval, and reranking without you touching OpenSearch or Weaviate. Knowledge bases are billed for indexing tokens plus OpenSearch storage. Vector databases start at $20/month with 1-click provisioning.

## Where Gradient Fits in the GPU Cloud Landscape

The honest comparison isn't "Gradient vs AWS" — it's "Gradient vs the mid-tier GPU clouds that most startups actually use." RunPod, Lambda Labs, CoreWeave, and Hyperstack all occupy roughly the same niche: cheaper than hyperscalers, simpler than running your own Kubernetes cluster on bare metal, but with varying reliability and feature depth.

Where Gradient tends to win is the integration story. RunPod is great for raw GPU rental, but if you want serverless inference, agents, and managed databases on the same platform with one bill, you're stitching together three or four vendors. Gradient bundles all of it. The tradeoff is that pure GPU pricing on DigitalOcean isn't always the absolute cheapest — RunPod's Community Cloud sometimes undercuts it on A100s — but the reliability and the surrounding tooling often make up the difference.

Lambda Labs is the other common comparison. It's generally cheaper per-GPU-hour, but availability is notoriously patchy and the product surface is narrower. Gradient sits in a useful middle ground: more expensive than the rock-bottom options, dramatically cheaper than AWS/GCP/Azure (DigitalOcean claims up to 80% lower cost than hyperscalers), and with a deeper feature set than the bare-GPU providers.

## GPU Droplets Pricing — Every Configuration Compared

DigitalOcean currently offers nine GPU configurations, ranging from entry-level single-GPU cards to 8-GPU HGX systems. Pricing below reflects on-demand rates; reserved pricing with longer commitments can push costs down significantly.

| GPU Model | GPU Memory | Droplet RAM | vCPUs | Storage | On-Demand Price | Get Started |
| --- | --- | --- | --- | --- | --- | --- |
| AMD Instinct MI350X | 288 GB | 256 GiB | 24 | 720 GiB boot + 5 TiB scratch | $6.89 / GPU / hr | [Launch GPU Droplet](https://bit.ly/DigitaLocean) |
| AMD Instinct MI350X ×8 | 2,304 GB | 2,048 GiB | 192 | 2,046 GiB + 40 TiB | ~$55 / hr (8×) | [Launch 8-GPU Node](https://bit.ly/DigitaLocean) |
| AMD Instinct MI325X | 256 GB | 164 GiB | 20 | 720 GiB + 5 TiB | $2.98 / GPU / hr | [Launch MI325X](https://bit.ly/DigitaLocean) |
| AMD Instinct MI325X ×8 | 2,048 GB | 1,310 GiB | 160 | 2,046 GiB + 40 TiB | $23.82 / hr | [Launch 8× MI325X](https://bit.ly/DigitaLocean) |
| AMD Instinct MI300X | 192 GB | 240 GiB | 20 | 720 GiB + 5 TiB | $2.59 / GPU / hr | [Launch MI300X](https://bit.ly/DigitaLocean) |
| AMD Instinct MI300X ×8 | 1,536 GB | 1,920 GiB | 160 | 2,046 GiB + 40 TiB | $20.70 / hr | [Launch 8× MI300X](https://bit.ly/DigitaLocean) |
| NVIDIA HGX B300 | 288 GB | 448 GiB | 28 | 720 GiB + 5 TiB | $10.39 / GPU / hr | [Launch B300](https://bit.ly/DigitaLocean) |
| NVIDIA HGX B300 ×8 | 2,304 GB | 3,584 GiB | 224 | 2,046 GiB + 40 TiB | $83.10 / hr | 👏 [Launch 8× B300](https://bit.ly/DigitaLocean) |
| NVIDIA HGX H200 | 141 GB | 240 GiB | 24 | 720 GiB + 5 TiB | $4.47 / GPU / hr | [Launch H200](https://bit.ly/DigitaLocean) |
| NVIDIA HGX H200 ×8 | 1,128 GB | 1,920 GiB | 192 | 2,046 GiB + 40 TiB | $35.78 / hr | [Launch 8× H200](https://bit.ly/DigitaLocean) |
| NVIDIA HGX H100 | 80 GB | 240 GiB | 20 | 720 GiB + 5 TiB | $4.41 / GPU / hr | [Launch H100](https://bit.ly/DigitaLocean) |
| NVIDIA HGX H100 ×8 | 640 GB | 1,920 GiB | 160 | 2,046 GiB + 40 TiB | $30.32 / hr | [Launch 8× H100](https://bit.ly/DigitaLocean) |
| NVIDIA RTX 4000 Ada | 20 GB | 32 GiB | 8 | 500 GiB NVMe | from ~$0.76 / GPU / hr | [Launch RTX 4000](https://bit.ly/DigitaLocean) |
| NVIDIA RTX 6000 Ada | 48 GB | 64 GiB | 8 | 500 GiB NVMe | from ~$1.10 / GPU / hr | [Launch RTX 6000](https://bit.ly/DigitaLocean) |
| NVIDIA L40S | 48 GB | 64 GiB | 8 | 500 GiB NVMe | from ~$1.91 / GPU / hr | [Launch L40S](https://bit.ly/DigitaLocean) |

A few notes on this table: the ×8 configurations are HGX systems, not eight separate Droplets — they share NVLink and a single high-memory pool, which matters a lot for large-model training. Reserved pricing can drop these rates by roughly 30-40% if you're willing to commit to a longer term. And all GPU Droplets come with a 99% uptime SLA, which puts DigitalOcean ahead of the cheaper community-cloud options that often offer no SLA at all.

## Serverless Inference Pricing — The Token Rates That Actually Matter

For most developers, serverless inference is where Gradient's economics get interesting. You pay per million tokens, with rates that track the upstream provider's pricing (no DigitalOcean markup on commercial models). Here are the headline rates for the most-used models:

| Model | Input (per 1M tokens) | Output (per 1M tokens) | Try Inference |
| --- | --- | --- | --- |
| Claude Sonnet 5 | $2.00 | $10.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| Claude Opus 5 | $5.00 | $25.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| Claude Haiku 4.5 | $1.00 | $5.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| GPT-5.5 (≤272K ctx) | $5.00 | $30.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| GPT-5.4 | $2.50 | $15.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| GPT-5 | $1.25 | $10.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| GPT-5 mini | $0.25 | $2.00 | [Start Inference](https://bit.ly/DigitaLocean) |
| DeepSeek V4 Pro 0813 | $1.32 | $3.96 | [Start Inference](https://bit.ly/DigitaLocean) |
| DeepSeek V4 Flash 0731 | $0.08 | $0.25 | [Start Inference](https://bit.ly/DigitaLocean) |
| GLM-5.2 (Z.ai) | $0.70 | $2.20 | [Start Inference](https://bit.ly/DigitaLocean) |
| Qwen 3.5 397B A17B | $0.55 | $3.50 | [Start Inference](https://bit.ly/DigitaLocean) |
| Llama 4 Maverick 17B 128E | $0.20 | $0.70 | [Start Inference](https://bit.ly/DigitaLocean) |
| Kimi K3 | $2.85 | $14.25 | [Start Inference](https://bit.ly/DigitaLocean) |

A few things worth flagging: prompt caching is supported across most models and offers substantial discounts on cached reads (often 80-90% off the input rate). Batch inference gives you up to 50% off on OpenAI and Anthropic models for non-real-time workloads — useful for evaluation pipelines, dataset enrichment, or content moderation at scale. And if you bring your own API keys for OpenAI or Anthropic, billing flows through the provider directly rather than DigitalOcean.

> Serverless inference is prepaid only — you need to maintain a positive balance, and the platform suspends access if it hits zero. Auto-reload is available if you'd rather not babysit the balance.

## Dedicated Inference — For Predictable, High-Volume Workloads

If your traffic is steady enough that you're paying more per-token than you would per-GPU-hour, dedicated inference makes more sense. You get a reserved GPU endpoint, BYOM support, and configurable scaling. Pricing tracks GPU Droplets closely:

| GPU | Dedicated Inference Rate | Deploy Dedicated |
| --- | --- | --- |
| AMD MI300X (1×) | $2.59 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| AMD MI300X (8×) | $20.70 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| AMD MI325X (1×) | $2.98 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| AMD MI325X (8×) | $23.82 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| AMD MI350X | $6.89 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| NVIDIA H100 (1×) | $4.41 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| NVIDIA H100 (8×) | $30.32 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| NVIDIA H200 (1×) | $4.47 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| NVIDIA H200 (8×) | $35.78 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| NVIDIA B300 (1×) | $10.39 / hr | [Deploy](https://bit.ly/DigitaLocean) |
| NVIDIA B300 (8×) | $83.10 / hr | [Deploy](https://bit.ly/DigitaLocean) |

## Agent Platform and Knowledge Base Costs

The Agent Platform itself is free to use — agent creation, evaluation runs against serverless candidates, and trace logging carry no separate charge. You pay for the underlying model tokens, knowledge base indexing/storage, and guardrails.

Knowledge base pricing breaks down as follows:

- **Embedding indexing**: ranges from $0.009 per 1M tokens (all-mini-lm-l6-v2) up to $0.09 per 1M tokens (gte-large-en-v1.5). The Qwen3 Embedding 0.6B model sits at $0.04 per 1M tokens, and BGE-M3 at $0.02.
- **Reranking**: $0.01 per 1M reranking tokens using BGE Reranker v2 m3.
- **Storage**: billed through managed OpenSearch (see OpenSearch pricing).
- **Retrieval queries**: same embedding rates as indexing.

Agent guardrails are cheap but not free: Content Moderation and Jailbreak Detection each run $0.20 per 1M tokens; Sensitive Data Detection is $0.34 per 1M tokens. Creating, editing, or duplicating guardrails carries no charge.

The Agent Development Kit (ADK) is currently free during public preview. When it reaches general availability, agent deployment hosting (measured in GiB-seconds) and judge-model tokens will be billed, but those costs are waived for now.

## The Broader DigitalOcean Stack — What Else Comes With the Account

One of the underrated things about Gradient is that it sits on top of the regular DigitalOcean cloud, so you get the rest of the product line included. CPU Droplets start at $4/month for a 1 vCPU / 512 MiB machine and scale up through Basic, CPU-Optimized, General Purpose, Memory-Optimized, and Storage-Optimized tiers. Managed Databases, Kubernetes (with a free control plane), App Platform, Spaces Object Storage, Volumes, and the standard networking and security primitives all live under the same console and bill.

Functions (serverless compute) include 90,000 GiB-seconds per month free — useful if you're wiring agent tool-calls back into lightweight backend logic. And the per-second billing model that DigitalOcean extended across Droplets means short-lived workloads (batch jobs, CI tests, ephemeral training runs) cost meaningfully less than on platforms that round up to the hour.

## The $200 Free Credit — How It Actually Works

This is the part most people care about and the part that's most often misdescribed. New accounts created through a referral link receive $200 in credit valid for 60 days. The credit auto-applies to your account — no coupon code needed — and can be spent across GPU Droplets, serverless inference, agent platform usage, and any other DigitalOcean product. After the credit is exhausted or the 60-day window closes, your registered payment method covers ongoing usage.

A couple of practical caveats: the credit doesn't apply to third-party API-key billing for OpenAI and Anthropic models (that flows through those providers directly), and serverless inference is prepaid-only, so you'll need to manually load the inference balance from your credit if you want to use it that way. The credit also doesn't roll over once the 60 days expire, so it's worth having a concrete plan for how to spend it — a model fine-tuning run, an agent evaluation suite, or a proof-of-concept inference endpoint all work well as use cases.

👉 [Claim the $200 credit and start building](https://bit.ly/DigitaLocean)

## Who Gradient Is Actually For

After laying out all the layers, it's worth being honest about the fit. Gradient works best for three audiences:

**Solo developers and small teams who don't want to wrangle AWS.** If your goal is "deploy DeepSeek R1 on an H100 and call it from a Python script," the 1-Click Models path gets you there in minutes. If you want to build an agent that answers questions over your own documents, the Agent Platform plus Knowledge Base combo handles the plumbing.

**Startups scaling past the prototype stage.** The integrated billing, the Inference Router for cost optimization, the evaluations tooling for model comparison, and the per-second billing all add up to a platform that grows with you without forcing a rewrite when you hit production traffic.

**Teams priced out of hyperscalers but wary of community clouds.** If you need an SLA, predictable availability, and a real product surface — but AWS pricing would eat your runway — Gradient hits a useful middle ground. The recent price increases on H100 (from $3.39 to $4.41) and H200 (from $3.44 to $4.47) stung a bit, but the rates remain well below hyperscaler equivalents.

Gradient is less compelling if you need absolute rock-bottom GPU pricing and don't care about the surrounding tooling — RunPod's Community Cloud will beat it on raw cost. It's also not the right pick if you need the full breadth of AWS services, edge regions, or deep enterprise compliance certifications. DigitalOcean has made progress on the compliance front, but the hyperscalers still lead there.

## Getting Started — A Quick Path Through the Stack

If you're new to the platform, the most efficient exploration path looks something like this:

1. Create an account through the referral link to claim the $200 credit.
2. Head to the Model Catalog and try a few serverless inference calls in the playground — Claude Sonnet 5, DeepSeek V4 Pro, and GLM-5.2 are good benchmarks to compare.
3. Spin up a GPU Droplet with a 1-Click Model (DeepSeek R1 or Llama 4 Maverick are popular starting points) to see what self-hosted inference feels like on dedicated hardware.
4. Build a simple agent in the Agent Platform with one knowledge base attached — point it at a small PDF or a few URLs.
5. Run an evaluation suite against the agent and watch the trace logs to see how routing and tool calls actually flow.

This sequence exercises most of the stack without committing serious spend, and by the end you'll have a clear sense of which layers you actually need.

## The Bottom Line

DigitalOcean Gradient AI doesn't try to compete with AWS on feature breadth, and it doesn't try to compete with RunPod on rock-bottom pricing. What it does is offer a coherent, integrated AI cloud that takes you from raw GPU access all the way up to production agents — with predictable billing, a real SLA, and a pricing model that scales down to a $4/month Droplet and up to an 8-GPU HGX B300 node. For the developer or small team that's tired of stitching together five different vendors to ship one AI feature, that coherence is worth a lot. And the $200 in starter credit means you can find out whether it fits your workload before you spend a cent of your own money.

👉 [Get started with DigitalOcean Gradient AI and claim $200 in free credit](https://bit.ly/DigitaLocean)
