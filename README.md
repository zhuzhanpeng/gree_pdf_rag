# gree_pdf_rag
# GREE-JKF-RAG 空调智能RAG问答系统
基于Python+FastAPI+Qdrant+Qwen轻量化大模型搭建的行业知识库问答项目，专为JKF风冷模块化机房空调产品手册打造。
支持**销售完整参数查询**、**客户脱敏轻量化咨询**双角色区分，Windows本地开发、Docker一键打包部署阿里云ECS，适合初学者完整实践RAG落地流程。

## 一、项目简介
### 1.1 项目痛点
企业销售查阅机房空调PDF手册效率低、对外技术话术不统一；客户重复咨询基础问题占用销售人力。
### 1.2 核心功能
1. PDF全自动解析、文本滑动窗口切片、工业文档文本提取
2. 中文专用向量检索：`BAAI/bge-small-zh-v1.5`，适配中文专业术语
3. 双角色Prompt隔离：销售输出完整参数/安装规范/样板案例；客户脱敏屏蔽工程尺寸、施工数据
4. 本地4bit量化大模型推理，低配Windows/阿里云服务器均可运行
5. 零前端框架原生HTML页面，开箱即用，无需额外前端开发
6. 全容器化Docker Compose部署，本地调试与线上环境完全一致

## 二、完整技术栈
### 本地开发环境（Win10）
- 系统：Windows 10
- Python：3.10
- 环境管理：Anaconda Conda
- IDE：PyCharm Community 免费社区版
- 容器工具：Docker Desktop + Docker Compose

### Python后端依赖
- Web服务：FastAPI + Uvicorn
- PDF解析：pdfplumber
- 向量数据库：Qdrant（本地持久化向量库）
- 中文嵌入模型：BAAI/bge-small-zh-v1.5
- LLM推理：transformers、accelerate、bitsandbytes（4bit量化）
- 页面渲染：Jinja2
- 文件上传：python-multipart

### 阿里云线上部署
- 服务器：ECS g8i.4xlarge 8核16G，500G SSD数据盘
- 系统：Alibaba Cloud Linux 3
- 安全体系：VPC内网隔离、安全组白名单、密钥登录、容器权限加固

## 三、项目目录结构
GREE-JKF-RAG/
- ├── .env # 环境变量密钥配置文件
- ├── Dockerfile # Docker 镜像构建配置
- ├── docker-compose.yml # 容器编排脚本
- ├── requirements.txt # Python 依赖清单
- ├── main.py # FastAPI 服务主入口
- ├── pdf_parser.py # PDF 文本解析、切片工具
- ├── vector_store.py # 向量库初始化、入库、检索逻辑
- ├── llm_service.py # 大模型推理、双角色 Prompt 模板
- ├── static/
- │ └── index.html # 前端问答网页
- ├── volumes/
- │ └── qdrant_db/ # 向量库持久化存储目录
- └── scripts/ # 备份、运维定时脚本


