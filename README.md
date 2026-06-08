<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=26&duration=3500&pause=800&color=58A6FF&center=true&vCenter=true&width=620&lines=UC+Berkeley+CS+%26+Applied+Math;Backend+%26+Distributed+Systems;ML+Infrastructure+at+Scale" alt="Typing SVG"/>
</p>

<p align="center">
  <a href="https://yijunxiang.com"><img src="https://img.shields.io/badge/Website-1F6FEB?style=for-the-badge&logo=googlechrome&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yijunxiang"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="https://scholar.google.com/citations?user=jiM91eYAAAAJ&hl=en"><img src="https://img.shields.io/badge/Google%20Scholar-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white"/></a>
  <a href="mailto:yijun.x.me@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/></a>
</p>

---

### Tech Stack

**Languages**<br>
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-CE422B?style=flat-square&logo=rust&logoColor=white)

**Infrastructure**<br>
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat-square&logo=amazonwebservices&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-0F9D9D?style=flat-square&logo=grpc&logoColor=white)

**Data & ML**<br>
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Ray](https://img.shields.io/badge/Ray-028CF0?style=flat-square&logo=ray&logoColor=white)

---

### Featured Work

**Enterprise Retail Platform** — event-driven microservices for multi-store retail.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#122B45','primaryTextColor':'#cfe8ff','primaryBorderColor':'#1F6FEB','lineColor':'#58A6FF','fontFamily':'monospace','fontSize':'14px'}}}%%
flowchart LR
  C([Client]) --> GW[Spring Cloud Gateway]
  GW --> OS[Order Service]
  GW --> IS[Inventory Service]
  OS -->|publish| KB[(Kafka Event Bus)]
  KB --> SG{Saga Orchestrator}
  SG -->|reserve| IS
  SG -->|charge| PS[Payment Service]
  SG -.->|compensate| OS
  IS --> RL[(Redis Locks)]
  OS --> DB[(PostgreSQL)]
```

<details>
<summary><b>Details</b></summary>
<br>

- 6 Spring Boot services with Eureka discovery, Spring Cloud Gateway, and a Kafka event bus
- Saga orchestration for order creation with compensating rollback; 12-state order state machine
- Redis distributed locks (SETNX + Lua atomic unlock) to prevent inventory overselling
- Cache-aside with scheduled warming, JWT auth with 4-tier RBAC

`Java 17` · `Spring Cloud` · `Kafka` · `Redis` · `PostgreSQL` · `Cassandra`

</details>

**Image Similarity Search** — distributed vector search at million scale.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#122B45','primaryTextColor':'#cfe8ff','primaryBorderColor':'#1F6FEB','lineColor':'#58A6FF','fontFamily':'monospace','fontSize':'14px'}}}%%
flowchart LR
  Q([Image Query]) --> API[FastAPI]
  API --> RC[(Redis Cache)]
  RC -.->|hit| API
  RC -->|miss| CLIP[CLIP Encoder]
  CLIP --> RT{Shard Router}
  RT --> S1[(Qdrant Shard 1)]
  RT --> S2[(Qdrant Shard 2)]
  RT --> S3[(Qdrant Shard 3)]
```

<details>
<summary><b>Details</b></summary>
<br>

- End-to-end ML pipeline with CLIP embeddings over a 30K+ image corpus
- 3-shard Qdrant cluster on ECS Fargate with multi-tier Redis caching (85%+ hit rate)
- Sustained throughput under 100+ concurrent users

`Python` · `FastAPI` · `PyTorch` · `Qdrant` · `Redis` · `AWS`

</details>

**Code Review Service** — automated code analysis with streaming feedback.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#122B45','primaryTextColor':'#cfe8ff','primaryBorderColor':'#1F6FEB','lineColor':'#58A6FF','fontFamily':'monospace','fontSize':'14px'}}}%%
flowchart LR
  C([Client]) --> FE[Next.js]
  FE --> GW[API Gateway]
  GW --> RLm[Rate Limiter]
  GW -->|stream| W[Analysis Workers]
  W --> AZ1[(Fargate AZ-1)]
  W --> AZ2[(Fargate AZ-2)]
```

<details>
<summary><b>Details</b></summary>
<br>

- Microservices backend with streaming responses, rate limiting, and 7-language support
- Deployed on ECS Fargate with auto-scaling and multi-AZ redundancy

`TypeScript` · `Next.js` · `FastAPI` · `Terraform` · `AWS`

</details>
