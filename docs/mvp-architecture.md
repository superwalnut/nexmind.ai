---
sidebar_position: 2
---

# Architecture

---

## 🧩 1. Overview

NexMind is an AI-powered business knowledge base and assistant. It allows businesses to upload internal documents and interact with them through a chat interface.

---

## 🌐 2. Tech Stack

| Layer            | Technology                        |
|------------------|------------------------------------|
| Frontend         | React + Tailwind + shadcn/ui       |
| Backend API      | FastAPI (Python) or Node.js (Express) |
| Authentication   | Clerk or Firebase Auth             |
| File Storage     | AWS S3 or Cloudinary               |
| Database         | PostgreSQL                         |
| Vector DB        | Pinecone / Weaviate / Qdrant       |
| AI Services      | OpenAI GPT-4o / Embedding API      |
| Hosting (Frontend)| Vercel / Netlify                  |
| Hosting (Backend)| Railway / Render / AWS Lambda      |

---

## 📁 3. Key Modules

### 3.1 Document Ingestion
- Drag-and-drop uploader
- Integrations: Google Drive, Dropbox (later)
- Auto parser for:
  - PDF
  - DOCX
  - TXT
  - Email text
- Store in S3, metadata in PostgreSQL
- Generate embeddings (OpenAI / local)

### 3.2 Vector Indexing
- Store document chunks in Pinecone/Weaviate
- Store `document_id`, `chunk_text`, `embedding`, and metadata

### 3.3 Chat Interface
- Simple React chat UI
- Send user input to backend
- Backend fetches relevant chunks via vector search
- Construct context + query → send to GPT-4o
- Return and display answer

### 3.4 Role-Based Access
- Users: Owner, Admin, Team Member
- Assign access to documents
- Secure chat responses based on access control

### 3.5 Knowledge Update Monitor (Phase 2)
- Detect changed files
- Re-chunk + re-embed changed content

---

## 🔐 4. Authentication & User Management
- Email/password or Google Sign-In via Clerk
- Team workspaces
- Invite team members
- Manage document visibility per user

---

## 💬 5. OpenAI Integration

- `text-embedding-3-small` or `text-embedding-ada-002` for vector DB
- GPT-4o for conversational response with context
- Prompt template includes:
  - Business name
  - Role of user (e.g., admin, staff)
  - Retrieved chunks
  - Query

---

## 🧪 6. MVP Milestones

| Phase      | Features                                   |
|------------|--------------------------------------------|
| Week 1-2   | Auth, file upload, chunking + embedding    |
| Week 3-4   | Vector search, chat UI, GPT-4o integration |
| Week 5     | Team roles + document access               |
| Week 6     | Polish UI, add waitlist/signup flow        |
| Week 7+    | Beta launch to selected businesses         |

---

## 🚀 7. Optional Enhancements (Post-MVP)

- Email forwarding for ingestion  
- Browser extension (chat with your docs anywhere)  
- Slack/Teams integration  
- Feedback on responses  
- Usage analytics & dashboard  
- Custom AI fine-tuning per business

---

## 🔧 8. DevOps & Deployment

- GitHub + CI/CD with Vercel / Railway
- Error tracking: Sentry
- Monitoring: UptimeRobot / Grafana (advanced)
- Secrets management: Doppler / AWS Secrets Manager

---

