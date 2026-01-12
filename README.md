# Plataforma Farmácia Virtual na AWS

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazonaws&logoColor=white)
![Status](https://img.shields.io/badge/status-estável-brightgreen)

Plataforma virtual de uma **farmácia fictícia** desenvolvida sobre a infraestrutura da **Amazon Web Services (AWS)**, com foco em boas práticas de arquitetura em nuvem, escalabilidade, segurança e alta disponibilidade.  
Projeto voltado para fins **acadêmicos e de portfólio técnico**.

---

## 📖 Visão Geral
_A aplicação simula um sistema de e-commerce farmacêutico, contemplando:_
- Autenticação de usuários  
- Catálogo de produtos  
- Carrinho de compras  
- Processamento de pedidos  
- Painel administrativo  
A solução aplica conceitos reais de computação em nuvem por meio de uma arquitetura em camadas utilizando serviços gerenciados da AWS.

---

## 🏗️ Diagrama de Arquitetura
```mermaid
flowchart TB
    U["Usuário / Navegador"]
    CF["Amazon CloudFront"]
    S3FE["Amazon S3 (Frontend)"]
    ALB["Application Load Balancer (opcional)"]
    APP["Amazon EC2 / AWS Elastic Beanstalk"]
    RDS["Amazon RDS (MySQL / PostgreSQL)"]

    U --> CF
    CF --> S3FE
    S3FE --> ALB
    ALB --> APP
    APP --> RDS

    subgraph Apoio["Serviços de Apoio"]
        IAM["Amazon IAM - Controle de permissões"]
        COG["Amazon Cognito - Autenticação de usuários"]
        S3AS["Amazon S3 - Imagens e arquivos"]
        CW["Amazon CloudWatch - Monitoramento e logs"]
    end

    APP --- IAM
    APP --- COG
    APP --- S3A
```
## 🏗️ Arquitetura da Solução
A plataforma é composta por três camadas principais:
1. Frontend (Apresentação):
- Amazon S3 (Static Website Hosting)
- Amazon CloudFront (CDN)

2. Backend (Aplicação):
- Amazon EC2 ou AWS Elastic Beanstalk
- API REST (Node.js, Python ou Java)

3. Banco de Dados (Dados):
- Amazon RDS (MySQL ou PostgreSQL)

4. Segurança e Gerenciamento:
- AWS IAM, Security Groups e VPC
- HTTPS via CloudFront ou Load Balancer

5. Monitoramento:
- Amazon CloudWatch

## 📑 Relatório de Implementação (Caminho e Conteúdo)
Arquivo: `RELATÓRIO.md`

O que o relatório contém:
- Contexto do projeto: objetivo de redução imediata de custos operacionais na AWS.
- Etapa 1 — Amazon EC2 Auto Scaling: ajuste automático de capacidade para eliminar recursos ociosos e reduzir custos de computação.
- Etapa 2 — Amazon S3 Intelligent-Tiering: otimização de armazenamento ao mover dados entre camadas de menor custo conforme padrão de acesso.
- Etapa 3 — AWS Cost Explorer & AWS Budgets: visibilidade, análise de consumo e controle proativo de gastos.
- Resultados esperados: economia imediata, maior eficiência de infraestrutura e governança financeira.

_Este relatório documenta decisões de arquitetura e práticas de FinOps, servindo como evidência de competências em otimização de custos, governança e operação em nuvem._

## 🚀 Tecnologias Utilizadas
- Frontend: HTML5, CSS3, JavaScript (ou React)
- Backend: Node.js / Python (Flask, Django) / Java (Spring Boot)
- Banco de Dados: MySQL ou PostgreSQL (Amazon RDS)
- Infraestrutura: AWS (EC2, S3, RDS, CloudFront, IAM, VPC, CloudWatch)

## ⚙️ Funcionalidades
- Cadastro e autenticação de usuários
- Listagem e busca de produtos
- Carrinho de compras
- Finalização de pedidos
- Administração de produtos e pedidos

## 🛠️ Implantação na AWS (Resumo)
1. Criar uma VPC com sub-redes públicas e privadas
2. Provisionar o Amazon RDS em sub-rede privada
3. Criar o Backend em EC2 ou Elastic Beanstalk
4. Hospedar o Frontend no Amazon S3
5. Configurar o CloudFront para distribuição global
6. Definir segurança com IAM e Security Groups
7. Ativar monitoramento com CloudWatch
8. O roteiro detalhado de implantação encontra-se na documentação do projeto.

## 🔐 Segurança
- Acesso ao banco restrito apenas às instâncias da aplicação
- Permissões mínimas com IAM Roles
- Comunicação criptografada via HTTPS
- Monitoramento contínuo com CloudWatch

## 📊 Monitoramento
- Métricas de CPU, memória e rede
- Logs da aplicação
- Alarmes configuráveis para incidentes
