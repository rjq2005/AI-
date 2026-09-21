# 个人作品集网站

一个使用原生 HTML、CSS、JavaScript 构建的个人作品集展示网站，面向教师、同学及招聘人员展示个人能力与项目成果。零依赖、零构建，双击即可运行。

## 功能特性

- **响应式布局**：桌面端左侧固定侧边栏 + 右侧滚动内容区；移动端（≤900px）自动切换为上下流式布局，无横向溢出
- **项目作品展示**：纵向连续排版（非卡片网格），图文左右交替，每个项目包含序号、名称、类别、时间、封面图、简介与技术栈标签
- **深浅色主题切换**：侧边栏一键切换，`localStorage` 记住用户选择，刷新无闪跳
- **导航高亮**：滚动时基于 `IntersectionObserver` 自动高亮当前浏览模块的导航项
- **平滑锚点滚动**：CSS `scroll-behavior: smooth` 实现
- **滚动入场动画**：模块/项目进入视口时轻微淡入上移
- **演示项目跳转**：每个作品的"查看项目"链接指向独立的完整演示页面

## 页面结构

| 模块 | 内容 |
|------|------|
| 个人信息与导航 | 头像、姓名、身份定位、个人简介、技能标签、锚点导航、主题切换按钮 |
| 项目作品 | 3 个完整项目（个人博客系统、极简天气应用、品牌视觉展示站） |
| 关于我 | 学习背景、能力方向、个人优势 |
| 联系方式 | 邮箱、电话、所在地、GitHub 等社交链接 |

## 目录结构

```
lab03/
├── index.html              # 作品集主页（入口）
├── css/
│   └── style.css           # 全部样式与响应式媒体查询
├── js/
│   └── script.js           # 主题切换、导航高亮、入场动画
├── assets/                 # 头像与项目封面占位图（SVG）
└── projects/               # 三个演示项目（均为独立原生页面）
    ├── blog-system/        # 个人博客系统（含 posts/ 5 篇完整文章页）
    ├── weather-app/        # 极简天气应用（可交互城市切换演示）
    └── brand-site/         # 品牌视觉展示站
```

## 技术栈

- **HTML5**：语义化标签（header / nav / main / article / footer）
- **CSS3**：CSS 自定义属性（主题变量）、Flexbox / Grid 布局、媒体查询、`object-fit`、`scroll-behavior`
- **JavaScript（原生 ES5+）**：`IntersectionObserver`、`localStorage`、DOM 操作
- 无任何前端框架、UI 组件库、图标库或 CDN 外链

## 运行方式

**方式一：直接打开**

双击根目录的 `index.html` 即可在浏览器中查看。

**方式二：本地服务器（推荐）**

```bash
# Python
python -m http.server 8000

# Node.js
npx serve .
```

然后访问 `http://localhost:8000`。

## 如何新增项目作品

复制 `index.html` 中任意一个 `<article class="project">…</article>` 区块，修改其中的序号、名称、类别、时间、封面图路径、简介和标签即可。若希望图片在另一侧，为 `<article>` 追加 `project--flip` 类。

## 自定义说明

- **替换占位图**：`assets/` 内为本地 SVG 占位图，将 `<img src="...">` 指向自己的图片即可，`object-fit: cover` 会自动保持比例整齐
- **修改个人信息**：姓名、简介、技能标签、联系方式均在 `index.html` 对应位置直接编辑
- **切换主题色**：强调色统一由 `css/style.css` 中的 `--accent` 变量控制，改一处即可全站生效

## 浏览器兼容

支持所有现代浏览器（Chrome、Edge、Firefox、Safari）。使用了 `IntersectionObserver`，不支持 IE11。
