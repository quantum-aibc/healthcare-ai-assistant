# healthcare-ai-assistant
Responsible healthcare information AI assistant built with Microsoft Azure AI Foundry, focusing on safe triage-style guidance, strict medical boundaries, and professional agent development practices.
# 🏥 Azure Healthcare AI Assistant (Information-Only, Non-Diagnostic)

A responsible **healthcare information assistant** built with **Microsoft Azure AI Foundry**.  
This project focuses on **safe, non-diagnostic health information** and structured guidance such as “self-care vs. consult a doctor vs. emergency”.

> ⚠️ **Disclaimer**  
> This assistant is for **educational and demonstration purposes only**.  
> It does **not** provide medical advice, diagnosis, or treatment.  
> Always consult a qualified healthcare professional for any medical concerns, and follow local emergency procedures in urgent situations.

---

## 🎯 Learning Focus

- Design of a **healthcare-safe agent persona** with:
  - Clear disclaimers and safety-first tone
  - Strict boundaries (no prescribing, no diagnosis)
  - Consistent reminders to contact real doctors

- Agent configuration in **Azure AI Foundry (Agents)**:
  - Parameters tuned for reliability (`temperature=0.3`, `top_p=0.5`)
  - Knowledge base integration over curated health FAQ content
  - Citation behavior enabled to show grounded sources

- Implementation of **safety & anti-hallucination**:
  - Refusal patterns for high-risk queries
  - Emergency trigger phrases (e.g., chest pain, severe bleeding)
  - Step-by-step guidance to seek in-person medical help

- Creation of **multiple persona variants**:
  - Calm nurse style
  - Clinic receptionist
  - Health coach
  - Pediatric-focused assistant
  - Senior-care-focused assistant

- Conversation management:
  - Handling of incomplete information
  - Re-asking clarifying questions
  - Safe fallbacks (“I’m not qualified to answer that”)

---

## 🧠 Use Case

The assistant can help with:

- General questions like:
  - “What is a migraine?”
  - “What are common flu symptoms?”
  - “How can I improve my sleep?”

- Triage-style guidance:
  - “Is this likely self-care, routine doctor visit, or emergency?”
  - Along with **strong reminders** to contact real healthcare providers.

---

## 🧱 Architecture Overview

- **Azure AI Foundry (Agents)**
  - System prompt encodes disclaimers + boundaries
  - Tools configured for FAQ lookup and triage rules
  - Citations from your curated KB where appropriate

- **Backend**
  - Python/FastAPI in `src/app.py`
  - `src/agent/healthcare_agent.py` implements:
    - Safety filters
    - Persona behavior
    - Tool orchestration

- **Tools**
  - `faq_health.py` – retrieves general health information from curated content
  - `triage_rules.py` – maps symptoms to high-level urgency bands
  - `safety_checks.py` – checks for red-flag symptoms and escalates

- **UI**
  - Simple chat-style web UI in `src/ui/web_app.py`

---

## 📁 Structure

```text
src/
  app.py
  agent/
    healthcare_agent.py
    variants/
      calm_nurse_style.py
      clinic_receptionist.py
      health_coach.py
      pediatric_focus.py
      senior_care_focus.py
  tools/
    faq_health.py
    triage_rules.py
    safety_checks.py
  config/
    settings.py
    logging_config.py
  ui/
    web_app.py

data/
  kb/
    general_health_faq.md
    emergency_signs.md
    lifestyle_advice.md

docs/
  persona.md
  boundaries.md
  safety_policy.md
  evaluation_plan.md
  model_optimization.md

tests/
  test_healthcare_agent.py
  test_safety_tools.py

notebooks/
  prompt_experiments.ipynb
