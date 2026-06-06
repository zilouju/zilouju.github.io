# 夏日小微博 · zilouju.github.io

轻量个人微博，部署在 GitHub Pages 上。

## 功能

- 发帖、评论、编辑、删除
- 数据保存在仓库 JSON 文件中，打开页面自动加载
- 首页优先加载最新内容，历史记录按需分页加载

## 数据文件

| 文件 | 说明 |
|------|------|
| `data/posts-recent.json` | 最新 20 条动态（首页快速加载） |
| `data/posts-archive.json` | 更早的历史动态（点击「加载更多」时拉取） |

## 发布配置（发帖需要）

GitHub Pages 是静态站点，写入数据需通过 GitHub API + Personal Access Token：

1. 打开 [创建 Token](https://github.com/settings/tokens/new?scopes=repo&description=weibo-pages)
2. 勾选 **repo** 权限，生成并复制 Token
3. 打开网站，点击右上角 **⚙️**，粘贴 Token 并保存

Token 仅保存在浏览器本地，不会上传到第三方。

未配置 Token 时为**只读模式**，可浏览已有内容。

## 本地预览

```bash
# 需要本地 HTTP 服务（直接打开 file:// 无法 fetch JSON）
python3 -m http.server 8080
# 访问 http://localhost:8080
```

## 部署

```bash
git add .
git commit -m "update weibo"
git push origin main
```

推送后约 1–2 分钟生效：https://zilouju.github.io/
