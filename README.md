# Fluxvoice
Open-source Voice-AI Reliability Infrastructure with a built-in agent runtime, real-world scenario testing, full call evaluation, and an automated agent-improvement engine.

## 🚨 Problem
AI agents perform well in test environments, but once deployed in production they often break. Enterprises have no way to see which calls failed, why they failed, or where the breakdown occurred. As a result, voice AI agents rarely scale beyond pilot projects.

## 💡 Solution
FluxVoice automatically generates real-world test scenarios before deployment, evaluates every production call to identify failures and their causes, and continuously analyzes these failures to feed fixes back into the system.

## 🎯 Absolute Core Values
1. It can run a voice agent.
2. It can detect failure in production.
3. It can show why agents failed.

## 🚀 MVP v0.1
### Agent Runtime Layer
> No advance routing. No complex flows.
1. LiveKit-based WebRTC runtime (self-hosted).
2. Real-time voice pipeline (STT, LLM, TTS)
3. Simple conversation loop (User speaks -> STT -> LLM -> TTS -> Respond)
4. Basic agent configuration (prompt + model selection).
5. Call lifecycle tracking (start/end) + event hooks.

### Observability and Evaluation Layer
> Rule-based detection only (no advanced AI evaluation yet).
1. Call logging (Call ID, Transcript, Timestamps, Latency per stage {STT, LLM, TTS}, Final status {Success/Failure}).
2. Basic failure detection (STT confidence < threshold, LLM response timeout, TTS error, Call ended without task completion, Latency > threshold).
3. Call dashboard (List of calls, Status {Success/Failure}, Failure type, Latency metrics, Transcript viewer).

### Pre-Deployment Testing
> No auto-fix yet — evaluation only.
1. Upload sample tarnscript or FAQ.
2. Generate 10-20 synthetic queries using LLM.
3. Run queries through agent pipeline.
4. Show Agent Response, Latency, Pass/Fail.

### UI structure
1. Agent UI (Conversation Interface)
2. Enterprise dashboard (Reliability UI)

## 🧱 Open-Source Software (OSS) Components

| Component | Default (Open-Source) |
|------------|----------------------|
| Speech-to-Text (STT) | `faster-whisper (CTranslate2)` |
| Text-to-Speech (TTS) | `Coqui XTTS v2` |
| LLM | `Llama 3 8B Instruct` |
| Runtime | `LiveKit (Self-hosted)` |

## 🐳 Deployment (MVP)

FluxVoice will use:
- Docker + Docker Compose
- Self-hosted LiveKit
- Self-hosted open-source models (default)
- Optional private provider (STT, LLM, TTS) integration

## Quick Start

```bash
git clone https://github.com/your-org/fluxvoice.git
cd fluxvoice
cp .env.example .env
docker compose up -d
```

Then open:

- Conversation UI → http://localhost:3000/agent
- Analytics UI → http://localhost:3000/dashboard

## 🧭 Roadmap

- Auto-fix engine (self-healing prompts)
- Advanced agent evaluation metrics
- Telephony (SIP/PSTN) support
- Provider plugin system
- Production-grade scaling
- Multi-OS support
