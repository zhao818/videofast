# 🎬 VideoFast — AI 口播视频生成

> 填文案，选模板，3 分钟出片。不用学剪辑，不用请团队。

[![License](https://img.shields.io/badge/license-CC%20BY--SA%204.0-blue)](LICENSE)
[![Deploy](https://img.shields.io/badge/deploy-GitHub%20Pages-brightgreen)](https://pages.github.com)

## ✨ 功能

- 🎤 **口播干货** — 痛点 + 反常识 + 三步拆解，适合知识博主
- 📦 **开箱带货** — 产品展示 + 效果对比 + CTA，适合电商卖家
- 📊 **数据报告** — 图表动画 + 结论提炼 + 指南，适合分析师

## 🚀 快速开始

1. Clone 仓库
```bash
git clone https://github.com/zhao818/videofast.git
```

2. 直接用浏览器打开 `index.html`，或部署到静态托管：
   - **GitHub Pages**：Settings → Pages → 选择 `main` 分支
   - **Vercel**：`vercel` 一键部署
   - **Netlify**：拖拽文件夹即可

## 🛠 技术栈

| 层级 | 技术 |
|------|------|
| 前端 | HTML / CSS / JavaScript（零依赖） |
| 后端 | [Supabase](https://supabase.com)（订单存储） |
| 支付 | 闲鱼 / 爱发电 |
| 部署 | GitHub Pages / Vercel / Netlify |

## 📦 Supabase 集成

后端使用 Supabase 存储订单。创建以下表：

```sql
CREATE TABLE orders (
  id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  template TEXT NOT NULL,
  title TEXT NOT NULL,
  subtitle TEXT,
  cards TEXT,
  contact TEXT NOT NULL,
  status TEXT DEFAULT 'pending',
  created_at TIMESTAMPTZ DEFAULT NOW()
);
```

在 `index.html` 中替换 `localStorage` 模拟为真实的 Supabase 调用：

```js
// 初始化 Supabase 客户端
import { createClient } from '@supabase/supabase-js'
const supabase = createClient('YOUR_SUPABASE_URL', 'YOUR_SUPABASE_ANON_KEY')

// 提交订单
const { data, error } = await supabase
  .from('orders')
  .insert([order])
```

## 💰 定价

| 方案 | 价格 | 内容 |
|------|------|------|
| 体验 | ¥9.9/次 | 1 条视频，720p 带水印，手动交付 |
| 包月 ⭐ | ¥99/月 | 30 条视频，1080p 无水印，优先交付 |
| Token 包 | ¥99/100 次 | 不过期，1080p 无水印，自助渲染 |

## 📄 许可

CC BY-SA 4.0 — 欢迎分享与二次创作，需署名并保留相同许可。

## 🔗 链接

- 网站：https://video.worldcorner.xyz
- 闲鱼店铺：[待补充]
- 爱发电：[待补充]
