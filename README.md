# Agent-Skills

Skills for AI agents — modular, reusable, and agent-ready.

面向 AI 智能体的技能集合：模块化、可复用、即装即用。

---

## 项目简介

本项目提供一个结构化的 Claude Agent Skills 仓库，用于组织和管理 AI 助手技能。每个技能独立封装，遵循统一的规范，便于复用和扩展。

### 核心理念

- **模块化设计** - 每个技能独立成目录，职责单一，便于维护
- **可复用性** - 标准化的技能格式，支持跨项目复用
- **即装即用** - 通过 marketplace.json 配置快速加载和分发
- **渐进式披露** - YAML 前置信息快速加载，完整指令按需读取

### 特性

- 标准技能结构，遵循 Anthropic 官方 Skills 开发指南
- 支持 Python/Bash 等多种脚本语言
- 本地缓存机制，提升响应速度
- 中文友好，文档和输出均支持中文

---

## 快速开始

### 前置要求

- Python 3.6+（如技能包含 Python 脚本）
- Claude Code 或支持 Agent Skills 的环境

### 使用技能

在 Claude Code 中，加载本项目的技能后，直接通过自然语言触发：

```
# 示例：使用中国节假日查询技能
"帮我查一下 2026 年的放假安排"
"今年国庆节怎么调休？"
```

技能会根据触发词自动激活，执行相应的工作流。

---

## 项目结构

```
agent-skills/
├── .claude-plugin/
│   └── marketplace.json          # 插件市场配置
├── skills/
│   └── <skill-name>/             # 技能目录
│       ├── SKILL.md              # 技能定义（YAML 前置信息 + Markdown 指令）
│       ├── scripts/              # 可执行脚本（可选）
│       │   └── <script>.py       # Python/Bash 等脚本
│       └── assets/               # 资源文件（可选）
│           ├── templates/        # 输出模板
│           └── cache/            # 缓存数据
├── README.md                     # 项目说明
└── LICENSE                       # 开源许可证
```

### 关键文件说明

| 文件/目录          | 作用                                       | 必须 |
| ------------------ | ------------------------------------------ | ---- |
| `SKILL.md`         | 技能定义文件，包含 YAML 前置信息和指令正文 | 是   |
| `scripts/`         | 存放技能依赖的可执行脚本                   | 否   |
| `assets/`          | 存放模板、缓存、数据等资源文件             | 否   |
| `marketplace.json` | 插件市场元数据配置                         | 是   |

---

## 已有技能

| 技能名称                                | 描述               | 触发词                                   |
| --------------------------------------- | ------------------ | ---------------------------------------- |
| [china-holidays](skills/china-holidays) | 中国法定节假日查询 | 节假日安排、放假通知、法定假日、调休安排 |

---

## 开发指南

关于如何创建新技能、编写脚本和配置插件市场，请参考以下官方指南：

- [Anthropic Skills 开发指南](Anthropic%20Official%20Skills%20Development%20Guide.md) - 技能结构与格式规范
- [Claude Code 插件市场开发者指南](Claude%20Code%20Marketplace%20Developer%20Guide.md) - 插件配置与发布流程

---

## 故障排查

### 技能未触发

**检查点：**
1. 确认 `SKILL.md` 的 `description` 字段包含触发关键词
2. 确认技能已在 `marketplace.json` 中注册
3. 尝试更明确的触发语句

---

## 贡献指南

欢迎提交新的技能！请确保：

1. 遵循标准技能结构
2. `SKILL.md` 包含完整的 YAML 前置信息
3. 提供清晰的使用示例
4. 脚本有适当的错误处理
