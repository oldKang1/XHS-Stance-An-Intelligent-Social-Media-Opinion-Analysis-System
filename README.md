# Cross-Platform Opinion Stance（跨平台观点立场分析系统）

## 项目简介

Cross-Platform Opinion Stance 是一个专门用于分析B站（Bilibili）视频评论情绪倾向的Web应用程序。该系统通过网络爬虫抓取视频评论，利用自然语言处理技术对评论进行情感分析，并以可视化的方式展示分析结果。

## 功能特性

- **B站评论爬取**：自动抓取指定B站视频的评论内容
- **情感分析**：使用预训练的深度学习模型对评论进行情绪分类（正面、负面、中性）
- **数据可视化**：直观展示情感分析结果和关键信息
- **实时监控**：提供爬取和分析过程的进度监控
- **关键词提取**：自动提取评论中的高频关键词

## 技术栈

- **后端框架**：Flask (Python)
- **前端技术**：HTML, CSS, JavaScript
- **爬虫引擎**：DrissionPage
- **NLP模型**：基于transformers的Erlangshen-Roberta-330M-Sentiment模型
- **数据处理**：Pandas, NumPy
- **可视化**：Chart.js

## 系统架构

```
┌─────────────────┐    ┌──────────────────┐    ┌──────────────────┐
│   B站网站       │───▶│  评论爬虫模块    │───▶│  情感分析模块    │
│ (数据源)        │    │   (blbl.py)      │    │ (comments_nlp.py)│
└─────────────────┘    └──────────────────┘    └──────────────────┘
                                                        │
                                                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌──────────────────┐
│   Web界面       │◀───│  Flask后端      │◀───│  数据处理模块    │
│ (templates)     │    │   (app.py)       │    │ (visualization)  │
└─────────────────┘    └──────────────────┘    └──────────────────┘
```

## 安装步骤

### 1. 环境要求

- Python 3.7+
- pip 包管理器

### 2. 克隆项目

```bash
git clone https://github.com/liuyikang/Cross-Platform-Opinion-Stance.git
cd Cross-Platform-Opinion-Stance
```

### 3. 安装依赖

```bash
pip install flask pandas numpy transformers torch DrissionPage datasets
```

### 4. 启动应用

```bash
cd app
python app.py
```

应用将在 `http://localhost:5000` 启动

## 使用指南

### 1. 视频评论爬取

1. 打开浏览器访问 `http://localhost:5000`
2. 在输入框中粘贴B站视频链接
3. 点击"开始爬取"按钮
4. 系统会自动打开无头浏览器访问视频页面并抓取评论
5. 爬取进度会在界面上实时显示

### 2. 情感分析

1. 爬取完成后，点击"开始分析"按钮
2. 系统将调用NLP模型对评论进行情感分析
3. 分析结果包括情感分布、关键词等
4. 进度条会显示分析进度

### 3. 结果查看

1. 点击"可视化"按钮进入结果展示页面
2. 查看情感分布饼图、关键词云、时间趋势图等
3. 所有图表均采用响应式设计，适配不同屏幕尺寸

## 文件结构

```
Cross-Platform Opinion Stance/
├── app/                    # 主应用目录
│   ├── app.py              # Flask主应用
│   ├── comments_nlp.py     # 情感分析模块
│   └── templates/          # HTML模板
│       ├── index.html      # 主页
│       ├── show.html       # 展示页
│       └── blbl.html       # B站分析页
├── data/                   # 数据处理目录
│   ├── blbl.py             # B站评论爬虫
│   ├── bili_comments.csv   # 爬取的原始评论数据
│   └── comments_nlp.csv    # 情感分析结果
├── visualization/          # 可视化模块
│   ├── pyspark_comments_visualization.py  # 评论可视化
│   └── pyspark_region_analysis.py         # 区域分析
└── README.md               # 项目说明文档
```

## 模型说明

本项目使用了哈工大（深圳）提供的中文情感分析模型 `IDEA-CCNL/Erlangshen-Roberta-330M-Sentiment`，该模型基于RoBERTa架构，在中文情感分析任务上有良好的表现。

## 数据存储

- **爬取数据**：存储在 `data/bili_comments.csv`
- **分析结果**：存储在 `data/comments_nlp.csv`
- **浏览器配置文件**：存储在 `data/bili_profile/`

## 项目特点

1. **自动化流程**：从评论爬取到情感分析实现全自动化处理
2. **实时反馈**：提供详细的进度提示和错误处理机制
3. **跨平台兼容**：支持Windows、Linux、macOS等主流操作系统
4. **中文优化**：针对中文文本进行专门优化，情感分析更准确
5. **可视化展示**：丰富的图表展示分析结果，直观易懂

## 注意事项

1. 使用时请遵守B站相关服务条款
2. 频繁爬取可能触发反爬机制，建议控制请求频率
3. 首次运行需要下载模型文件，可能需要较长时间
4. 确保网络连接稳定，避免爬取过程中断

## 维护者

**刘奕康**

## 许可证

MIT License

## 更新日志

### v1.0.0
- 实现基础评论爬取功能
- 集成情感分析模型
- 完成Web界面开发
- 添加数据可视化功能

---

*该项目仅供学习和研究使用，请合理合法地使用相关功能。*
