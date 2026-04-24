# 前端网站规划 - CURSOR API 文档

## 目标
将 `/data/openclaw/apiwebsite/CURSOR API 接口对接4.23 .apifox.json`（17.5MB）中的 339 个 API 端点转换为 React 前端网站

## 技术选型
- React 18 + TypeScript + Vite + Tailwind CSS
- 纯前端，无需后端
- 类似 Stripe/OpenAPI 文档风格

## 站点结构
```
首页（分类卡片 + 搜索）
├── 分类列表（14个分类，每个展示该分类下的API卡片）
├── API 详情页（方法+端点、描述、请求头、请求体 Schema、响应示例、curl 命令）
├── 搜索结果页（全文搜索 API 名称/路径/描述）
├── 配置指南（Python / Node.js / PHP 示例代码）
└── Sidebar 可折叠分类导航
```

## 数据提取状态
- ✅ 已完成：`/data/openclaw/apiwebsite/client/api_data.js`（3.6MB）
- 339 APIs, 14 categories
- 分类已分组，方法已提取

## 文件清单（已创建在 /data/openclaw/apiwebsite/client/src/）

### 类型 & 工具
- `src/types/api.ts` — ApiEndpoint, CategoryInfo, Schema, 方法色标
- `src/utils/search.ts` — searchApis, highlightMatch
- `src/api_data.js` — 导出 API_DATA（3.6MB）

### 组件（8个）
- `components/Layout.tsx` — 布局容器（Sidebar + Header + main）
- `components/Sidebar.tsx` — 分类导航侧边栏（可折叠）
- `components/Header.tsx` — 顶栏（搜索框）
- `components/SearchBar.tsx` — 搜索输入（⌘K 快捷键）
- `components/MethodBadge.tsx` — GET/POST/PUT/DELETE 色标
- `components/APICard.tsx` — API 卡片（点击跳转详情）
- `components/SchemaViewer.tsx` — JSON Schema 可折叠树
- `components/CodeBlock.tsx` — 代码块 + 复制按钮
- `components/ParameterTable.tsx` — 参数表格

### 页面（5个）
- `pages/Home.tsx` — 首页：统计卡片 + 14个分类卡片
- `pages/Category.tsx` — 分类列表：API 卡片网格 + 搜索过滤
- `pages/APIDetail.tsx` — 详情：curl 示例 + 参数表 + Schema + 响应
- `pages/ConfigGuide.tsx` — Python/Node.js/PHP 配置代码
- `pages/SearchResults.tsx` — 搜索聚合结果

### 路由 & 入口
- `routes/index.tsx` — react-router 路由配置
- `App.tsx` — 根组件
- `main.tsx` — 入口
- `index.css` — Tailwind + 全局样式

## 待解决
- Tailwind CSS 依赖 npm install 失败（系统 OOM kill）
- 需要：npm install tailwindcss autoprefixer postcss

## 339 APIs 分类统计
| 分类 | 数量 |
|---|---|
| 聊天(Chat) | 68 |
| 视频模型 | 53 |
| 可灵 Kling 平台 | 50 |
| 绘画模型 | 45 |
| Replicate 聚合平台 | 32 |
| Fal-ai 聚合平台 | 28 |
| 文生音乐 Suno | 23 |
| MiniMax官方 | 12 |
| 聊天(Responses) | 7 |
| Vidu 官方 | 9 |
| 系统API | 9 |
| Rerank | 1 |
| 帮助中心 | 1 |
| GPTs 相关 | 1 |
