# terraform-dev-container

https://space.bilibili.com/364122352/channel/series


<html><head>
<meta charset="utf-8">
<title>9个Docker最佳实践，让你的容器更安全高效 - 善忘技术夹</title>
        <meta name="keywords" content="善用佳软">

    <body>
<header>
    <div class="banner">
        <div class="fn-clear wrapper">
            <h1 class="fn-inline">
                <a href="https://www.swjsj.com" rel="start">
                    善忘技术夹
                </a>
            </h1>
            <small> &nbsp; 善忘是一种境界|学习|分享|创造美好生活</small>
            <div class="fn-right">
                    <a href="/login?goto=https%3A%2F%2Fwww.swjsj.com%2Fadmin-index.do%23main">
                        <i class="icon-login"></i> 登录
                    </a>
                    <a href="https://www.swjsj.com/register">
                        <i class="icon-register"></i> 注册
                    </a>
            </div>
        </div>
    </div>

    <div class="navbar">
        <div class="fn-clear wrapper">
            <nav class="fn-left">
                <a href="https://www.swjsj.com">
                    <i class="icon-home"></i>
                    首页
                </a>
                <a href="https://www.swjsj.com/dynamic.html" rel="section">
                    <i class="icon-refresh"></i> 动态
                </a>
                <a href="https://www.swjsj.com/tags.html" rel="section">
                    <i class="icon-tags"></i> 标签墙
                </a>
                <a href="https://www.swjsj.com/archives.html">
                    <i class="icon-inbox"></i> 存档
                </a>
                <a rel="archive" href="https://www.swjsj.com/links.html">
                    <i class="icon-link"></i> 友情链接
                </a>
                <a rel="alternate" href="https://www.swjsj.com/blog-articles-rss.do">
                    <i class="icon-rss"></i> RSS
                </a>
            </nav>
        </div>
    </div>
</header>
<div class="responsive fn-none">
    <i class="icon-list"></i>
    <ul class="list">
                <li>
                    <a href="/login?goto=https%3A%2F%2Fwww.swjsj.com%2Fadmin-index.do%23main">
                        <i class="icon-login"></i> 登录
                    </a>
                </li>
                <li>
                    <a href="https://www.swjsj.com/register">
                        <i class="icon-register"></i> 注册
                    </a>
                </li>
        <li>
            <a href="https://www.swjsj.com">
                <i class="icon-home"></i>
                首页
            </a>
        </li>
        <li>
            <a href="https://www.swjsj.com/dynamic.html" rel="section">
                <i class="icon-refresh"></i> 动态
            </a>
        </li>
        <li>
            <a href="https://www.swjsj.com/tags.html" rel="section">
                <i class="icon-tags"></i> 标签墙
            </a>
        </li>
        <li>
            <a href="https://www.swjsj.com/archives.html">
                <i class="icon-inbox"></i> 存档
            </a>
        </li>
        <li>
            <a rel="archive" href="https://www.swjsj.com/links.html">
                <i class="icon-link"></i> 友情链接
            </a>
        </li>
        <li>
            <a rel="alternate" href="https://www.swjsj.com/blog-articles-rss.do">
                <i class="icon-rss"></i> RSS
            </a>
        </li>
    </ul>
</div>        <div class="wrapper">
            <div class="main-wrap">
                <main>
                    <article class="post">
                        <header>
                            <h1>
                                <a rel="bookmark" href="https://www.swjsj.com/articles/2026/01/26/1769435860984.html">
                                    9个Docker最佳实践，让你的容器更安全高效
                                </a>
                            </h1>
                            <div class="meta">
                                <span class="tooltipped tooltipped-n" aria-label="创建日期">
                                    <i class="icon-date"></i>
                                    <time>
                                        2026-01-26
                                    </time>
                                </span>
                                                &nbsp; | &nbsp;
                                                <span class="tooltipped tooltipped-n" aria-label="评论数">
                                    <i class="icon-comments"></i>
                                    <a href="https://www.swjsj.com/articles/2026/01/26/1769435860984.html#comments">
                                        0 评论</a>
                                </span>
                                                &nbsp; | &nbsp;
                                                <span class="tooltipped tooltipped-n" aria-label="浏览数">
                                    <i class="icon-views"></i>
                                    616 浏览
                                </span>
                            </div>
                        </header>

                        <div class="content-reset">
                            <link rel="stylesheet" type="text/css" href="https://www.swjsj.com/plugins/list/style.css"><ul class="b3-solo-list"><li class="b3-solo-list-h2"><a href="#b3_solo_h2_0">使用官方镜像</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_1">常用官方镜像</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_2">指定具体版本</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_3">版本号建议</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_4">多阶段构建</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_5">效果对比</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_6">使用.dockerignore</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_7">.dockerignore示例</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_8">效果</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_9">使用最小权限用户</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_10">环境变量配置</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_11">优化缓存利用率</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_12">效果对比</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_13">给镜像打标签</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_14">扫描镜像漏洞</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_15">扫描工具</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_16">集成到CI/CD</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_17">完整示例：优秀Dockerfile</a></li><li class="b3-solo-list-h3"><a href="#b3_solo_h3_18">.dockerignore</a></li><li class="b3-solo-list-h2"><a href="#b3_solo_h2_19">总结</a></li></ul><p style="max-width: 380px;"><img src="https://assets.bytebytego.com/diagrams/0016-9-docker-best-practices-you-must-know.png" alt=""></p>
<p style="max-width: 380px;">Docker已经成为容器化的事实标准，但很多人用Docker的方式很有问题。镜像体积大、构建慢、安全性差…今天分享9个必须知道的Docker最佳实践。</p>
<p style="max-width: 380px;">我见过太多Dockerfile写得一塌糊涂，镜像几个GB，部署等到崩溃，用root用户跑应用安全风险巨大，构建一次要10分钟。</p>
<hr>
<span id="b3_solo_h2_0"></span><h2><a href="#使用官方镜像" id="使用官方镜像"></a>使用官方镜像</h2>
<p style="max-width: 380px;"><strong>能从官方拿，就不要自己造。</strong></p>
<pre><code class="hljs">自己构建基础镜像：
→ 可能有安全漏洞
→ 更新不及时
→ 兼容性问题

官方镜像：
→ 社区维护，定期更新
→ 安全漏洞修复快
→ 经过充分测试
</code></pre>
<span id="b3_solo_h3_1"></span><h3><a href="#常用官方镜像" id="常用官方镜像"></a>常用官方镜像</h3>
<table>
<thead>
<tr><th> 镜像 </th><th> 用途 </th></tr>
</thead>
<tbody>
<tr><td> node </td><td> Node.js应用 </td></tr>
<tr><td> openjdk </td><td> Java应用 </td></tr>
<tr><td> python </td><td> Python应用 </td></tr>
<tr><td> nginx </td><td> Web服务器 </td></tr>
<tr><td> postgresql </td><td> PostgreSQL数据库 </td></tr>
<tr><td> redis </td><td> Redis缓存 </td></tr>
</tbody>
</table>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ✅ 推荐</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18</span>-alpine

<span class="hljs-comment"># ❌ 不推荐</span>
<span class="hljs-keyword">FROM</span> my-custom-base-image
</code></pre>
<hr>
<span id="b3_solo_h2_2"></span><h2><a href="#指定具体版本" id="指定具体版本"></a>指定具体版本</h2>
<p style="max-width: 380px;"><strong>永远不要用latest标签。</strong></p>
<pre><code class="hljs css">今天构建用的是<span class="hljs-selector-tag">node</span><span class="hljs-selector-pseudo">:18</span>
明天构建可能变成<span class="hljs-selector-tag">node</span><span class="hljs-selector-pseudo">:19</span>
应用炸了

<span class="hljs-selector-tag">latest</span>指向最新的版本，你根本不知道会拉到什么版本
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ✅ 好</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18.17</span>.<span class="hljs-number">0</span>-alpine

<span class="hljs-comment"># ❌ 坏</span>
<span class="hljs-keyword">FROM</span> node:latest
</code></pre>
<span id="b3_solo_h3_3"></span><h3><a href="#版本号建议" id="版本号建议"></a>版本号建议</h3>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># 最严格：主版本.次版本.补丁版本</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18.17</span>.<span class="hljs-number">0</span>-alpine

<span class="hljs-comment"># 次严格：主版本.次版本（允许补丁更新）</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18.17</span>-alpine

<span class="hljs-comment"># 一般情况：主版本</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18</span>-alpine
</code></pre>
<p style="max-width: 380px;">看你对稳定性的要求选择。</p>
<hr>
<span id="b3_solo_h2_4"></span><h2><a href="#多阶段构建" id="多阶段构建"></a>多阶段构建</h2>
<p style="max-width: 380px;"><strong>大幅减小镜像体积的神器。</strong></p>
<pre><code class="hljs coffeescript">构建Node.js应用：
需要安装<span class="hljs-built_in">npm</span>依赖
需要编译TypeScript
需要打包前端资源

这些东西在运行时根本不需要
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ===== 构建阶段 =====</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18</span> AS builder
<span class="hljs-keyword">WORKDIR</span> <span class="bash">/app
</span><span class="hljs-keyword">COPY</span> <span class="bash">package*.json ./
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm ci
</span><span class="hljs-keyword">COPY</span> <span class="bash">. .
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm run build
</span>
<span class="hljs-comment"># ===== 运行阶段 =====</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18</span>-alpine
<span class="hljs-keyword">WORKDIR</span> <span class="bash">/app
</span><span class="hljs-keyword">COPY</span> <span class="bash">--from=builder /app/dist ./dist
</span><span class="hljs-keyword">COPY</span> <span class="bash">package*.json ./
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm ci --production
</span><span class="hljs-keyword">CMD</span> <span class="bash">[<span class="hljs-string">"node"</span>, <span class="hljs-string">"dist/index.js"</span>]
</span></code></pre>
<span id="b3_solo_h3_5"></span><h3><a href="#效果对比" id="效果对比"></a>效果对比</h3>
<table>
<thead>
<tr><th> 方式 </th><th> 镜像体积 </th></tr>
</thead>
<tbody>
<tr><td> 单阶段构建 </td><td> 800MB </td></tr>
<tr><td> 多阶段构建 </td><td> 150MB </td></tr>
</tbody>
</table>
<p style="max-width: 380px;">减少了85%。</p>
<hr>
<span id="b3_solo_h2_6"></span><h2><a href="#使用dockerignore" id="使用dockerignore"></a>使用.dockerignore</h2>
<p style="max-width: 380px;"><strong>不需要的文件别拷进镜像。</strong></p>
<pre><code class="hljs css">构建镜像时，<span class="hljs-selector-tag">Docker</span>会把整个上下文都拷进去
包括<span class="hljs-selector-tag">node_modules</span>（几<span class="hljs-selector-tag">GB</span>）、<span class="hljs-selector-class">.git</span>（几百<span class="hljs-selector-tag">MB</span>）...

构建慢、镜像大，没必要
</code></pre>
<span id="b3_solo_h3_7"></span><h3><a href="#dockerignore示例" id="dockerignore示例"></a>.dockerignore示例</h3>
<pre><code class="hljs css"><span class="hljs-selector-tag">node_modules</span>
<span class="hljs-selector-tag">npm-debug</span><span class="hljs-selector-class">.log</span>
<span class="hljs-selector-class">.git</span>
<span class="hljs-selector-class">.gitignore</span>
<span class="hljs-selector-tag">README</span><span class="hljs-selector-class">.md</span>
<span class="hljs-selector-class">.env</span>
<span class="hljs-selector-class">.env</span><span class="hljs-selector-class">.local</span>
<span class="hljs-selector-tag">tests</span>
*<span class="hljs-selector-class">.md</span>
<span class="hljs-selector-tag">coverage</span>
</code></pre>
<span id="b3_solo_h3_8"></span><h3><a href="#效果" id="效果"></a>效果</h3>
<pre><code class="hljs css">没有<span class="hljs-selector-class">.dockerignore</span>：
构建上下文大小：2<span class="hljs-selector-class">.5GB</span>
构建时间：8分钟

使用<span class="hljs-selector-class">.dockerignore</span>：
构建上下文大小：50<span class="hljs-selector-tag">MB</span>
构建时间：30秒
</code></pre>
<hr>
<span id="b3_solo_h2_9"></span><h2><a href="#使用最小权限用户" id="使用最小权限用户"></a>使用最小权限用户</h2>
<p style="max-width: 380px;"><strong>默认root用户风险很大。</strong></p>
<pre><code class="hljs">容器被攻破
→ 如果是root用户
→ 攻击者可以做任何事
→ 可以修改系统文件
→ 可以安装恶意软件
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ✅ 使用非root用户</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18</span>-alpine

<span class="hljs-comment"># 创建专门的用户</span>
<span class="hljs-keyword">RUN</span> <span class="bash">addgroup -g 1001 -S nodejs
</span><span class="hljs-keyword">RUN</span> <span class="bash">adduser -S nodejs -u 1001
</span>
<span class="hljs-comment"># 切换到该用户</span>
<span class="hljs-keyword">USER</span> nodejs

<span class="hljs-keyword">WORKDIR</span> <span class="bash">/app
</span><span class="hljs-keyword">COPY</span> <span class="bash">--chown=nodejs:nodejs package*.json ./
</span></code></pre>
<table>
<thead>
<tr><th> 用户 </th><th> 容器逃逸风险 </th></tr>
</thead>
<tbody>
<tr><td> root </td><td> 高，可以完全控制宿主机 </td></tr>
<tr><td> 非root </td><td> 低，只能做受限操作 </td></tr>
</tbody>
</table>
<hr>
<span id="b3_solo_h2_10"></span><h2><a href="#环境变量配置" id="环境变量配置"></a>环境变量配置</h2>
<p style="max-width: 380px;"><strong>通过环境变量实现配置外部化。</strong></p>
<pre><code class="hljs markdown">同一镜像不同环境：
<span class="hljs-bullet">- </span>开发环境：一套环境变量
<span class="hljs-bullet">- </span>测试环境：另一套环境变量
<span class="hljs-bullet">- </span>生产环境：又一套环境变量

镜像不用重新构建
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># Dockerfile</span>
<span class="hljs-keyword">ENV</span> NODE_ENV=production
<span class="hljs-keyword">ENV</span> PORT=<span class="hljs-number">3000</span>
<span class="hljs-keyword">ENV</span> DB_HOST=mongodb
</code></pre>
<pre><code class="language-yaml"># docker-compose.yml
services:
  app:
    image: myapp:1.0
    environment:
      - NODE_ENV=development
      - PORT=3000
      - DB_HOST=localhost
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># Dockerfile设置默认值，docker-compose覆盖</span>
<span class="hljs-keyword">ENV</span> NODE_ENV=production
environment:
  - NODE_ENV=${NODE_ENV:-production}
</code></pre>
<hr>
<span id="b3_solo_h2_11"></span><h2><a href="#优化缓存利用率" id="优化缓存利用率"></a>优化缓存利用率</h2>
<p style="max-width: 380px;"><strong>把变化少的放前面，变化多的放后面。</strong></p>
<pre><code class="hljs">Docker构建时，每一层都会被缓存
如果这一层没变化，就用缓存
如果变化了，这层和后面所有层都要重新构建
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ❌ 缓存利用率低</span>
<span class="hljs-keyword">COPY</span> <span class="bash">. .
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm ci
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm run build
</span></code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ✅ 缓存利用率高</span>
<span class="hljs-keyword">COPY</span> <span class="bash">package*.json ./
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm ci
</span><span class="hljs-keyword">COPY</span> <span class="bash">src ./src
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm run build
</span></code></pre>
<span id="b3_solo_h3_12"></span><h3><a href="#效果对比" id="效果对比"></a>效果对比</h3>
<pre><code class="hljs">修改一行代码：

错误做法：
→ 拷贝代码（重新构建）
→ 安装依赖（重新构建，耗时2分钟）
→ 构建应用（重新构建，耗时1分钟）
总计：3分钟

正确做法：
→ 依赖没变，用缓存
→ 拷贝代码（重新构建）
→ 构建应用（重新构建，耗时1分钟）
总计：1分钟
</code></pre>
<hr>
<span id="b3_solo_h2_13"></span><h2><a href="#给镜像打标签" id="给镜像打标签"></a>给镜像打标签</h2>
<p style="max-width: 380px;"><strong>标签要有意义，方便管理。</strong></p>
<pre><code class="language-bash hljs"><span class="hljs-comment"># 版本标签</span>
docker tag myapp:1.0.0 myapp:1
docker tag myapp:1.0.0 myapp:latest

<span class="hljs-comment"># 环境标签</span>
docker tag myapp:1.0.0 myapp:dev
docker tag myapp:1.0.0 myapp:staging
docker tag myapp:1.0.0 myapp:prod

<span class="hljs-comment"># Git提交标签</span>
docker tag myapp:1.0.0 myapp:git-abc123
</code></pre>
<pre><code class="language-dockerfile hljs"><span class="hljs-keyword">LABEL</span> <span class="bash">maintainer=<span class="hljs-string">"your-email@example.com"</span>
</span><span class="hljs-keyword">LABEL</span> <span class="bash">version=<span class="hljs-string">"1.0.0"</span>
</span><span class="hljs-keyword">LABEL</span> <span class="bash">description=<span class="hljs-string">"My awesome application"</span>
</span><span class="hljs-keyword">LABEL</span> <span class="bash">org.opencontainers.image.source=<span class="hljs-string">"https://github.com/user/repo"</span>
</span></code></pre>
<pre><code class="language-bash hljs">docker inspect myapp:1.0.0 | grep -A 10 <span class="hljs-string">"Labels"</span>
</code></pre>
<hr>
<span id="b3_solo_h2_14"></span><h2><a href="#扫描镜像漏洞" id="扫描镜像漏洞"></a>扫描镜像漏洞</h2>
<p style="max-width: 380px;"><strong>上线前必须扫描。</strong></p>
<pre><code class="hljs">你以为基础镜像是安全的？
官方镜像也可能有漏洞

2019年发现的一个漏洞
影响了数百万个容器
只是因为大家用的基础镜像没及时更新
</code></pre>
<span id="b3_solo_h3_15"></span><h3><a href="#扫描工具" id="扫描工具"></a>扫描工具</h3>
<p style="max-width: 380px;"><strong>Docker内置扫描</strong></p>
<pre><code class="language-bash hljs">docker scan myapp:1.0.0

<span class="hljs-comment"># 输出示例：</span>
✗ High: CVE-2023-1234 <span class="hljs-keyword">in</span> openssl
✗ Medium: CVE-2023-5678 <span class="hljs-keyword">in</span> node
✓ Low: CVE-2023-9012 <span class="hljs-keyword">in</span> libssl
</code></pre>
<p style="max-width: 380px;"><strong>Trivy（推荐）</strong></p>
<pre><code class="language-bash hljs">brew install trivy
trivy image myapp:1.0.0
trivy image --format json --output result.json myapp:1.0.0
</code></pre>
<span id="b3_solo_h3_16"></span><h3><a href="#集成到cicd" id="集成到cicd"></a>集成到CI/CD</h3>
<pre><code class="language-yaml"># GitHub Actions示例
- name: Build image
  run: docker build -t myapp:${{ github.sha }} .

- name: Scan image
  run: |
    trivy image --exit-code 1 --severity HIGH,CRITICAL myapp:${{ github.sha }}

# 发现高危漏洞，构建直接失败
</code></pre>
<hr>
<span id="b3_solo_h2_17"></span><h2><a href="#完整示例优秀dockerfile" id="完整示例优秀dockerfile"></a>完整示例：优秀Dockerfile</h2>
<pre><code class="language-dockerfile hljs"><span class="hljs-comment"># ==================== 构建阶段 ====================</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18.17</span>.<span class="hljs-number">0</span>-alpine AS builder

<span class="hljs-keyword">WORKDIR</span> <span class="bash">/app
</span><span class="hljs-keyword">COPY</span> <span class="bash">package*.json ./
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm ci --only=production
</span><span class="hljs-keyword">COPY</span> <span class="bash">. .
</span><span class="hljs-keyword">RUN</span> <span class="bash">npm run build
</span>
<span class="hljs-comment"># ==================== 运行阶段 ====================</span>
<span class="hljs-keyword">FROM</span> node:<span class="hljs-number">18.17</span>.<span class="hljs-number">0</span>-alpine

<span class="hljs-keyword">LABEL</span> <span class="bash">maintainer=<span class="hljs-string">"your-email@example.com"</span>
</span><span class="hljs-keyword">LABEL</span> <span class="bash">version=<span class="hljs-string">"1.0.0"</span>
</span><span class="hljs-keyword">LABEL</span> <span class="bash">description=<span class="hljs-string">"My Node.js Application"</span>
</span>
<span class="hljs-keyword">RUN</span> <span class="bash">addgroup -g 1001 -S nodejs &amp;&amp; \
    adduser -S nodejs -u 1001
</span>
<span class="hljs-keyword">WORKDIR</span> <span class="bash">/app
</span><span class="hljs-keyword">COPY</span> <span class="bash">--from=builder --chown=nodejs:nodejs /app/dist ./dist
</span><span class="hljs-keyword">COPY</span> <span class="bash">--from=builder --chown=nodejs:nodejs /app/node</span><em><span class="bash">modules ./node</span><em><span class="bash">modules
</span><span class="hljs-keyword">COPY</span> <span class="bash">--chown=nodejs:nodejs package*.json ./
</span>
<span class="hljs-keyword">USER</span> nodejs

<span class="hljs-keyword">ENV</span> NODE_ENV=production
<span class="hljs-keyword">ENV</span> PORT=<span class="hljs-number">3000</span>

<span class="hljs-keyword">EXPOSE</span> <span class="hljs-number">3000</span>

HEALTHCHECK --interval=30s --timeout=3s \
  <span class="hljs-keyword">CMD</span> <span class="bash">node <span class="hljs-_">-e</span> <span class="hljs-string">"require('http').get('http://localhost:3000/health', (r) =&gt; {process.exit(r.statusCode === 200 ? 0 : 1)})"</span>
</span>
<span class="hljs-keyword">CMD</span> <span class="bash">[<span class="hljs-string">"node"</span>, <span class="hljs-string">"dist/index.js"</span>]
</span></em></em></code></pre><em><em>
<span id="b3_solo_h3_18"></span><h3><a href="#dockerignore" id="dockerignore"></a>.dockerignore</h3>
<pre><code class="hljs css"><span class="hljs-selector-tag">node_modules</span>
<span class="hljs-selector-tag">npm-debug</span><span class="hljs-selector-class">.log</span>
<span class="hljs-selector-class">.git</span>
<span class="hljs-selector-class">.gitignore</span>
<span class="hljs-selector-tag">README</span><span class="hljs-selector-class">.md</span>
<span class="hljs-selector-class">.env</span>
<span class="hljs-selector-class">.env</span><span class="hljs-selector-class">.local</span>
<span class="hljs-selector-class">.env</span>.*<span class="hljs-selector-class">.local</span>
<span class="hljs-selector-tag">tests</span>
*<span class="hljs-selector-class">.md</span>
<span class="hljs-selector-tag">coverage</span>
<span class="hljs-selector-class">.vscode</span>
<span class="hljs-selector-class">.idea</span>
<span class="hljs-selector-tag">dist</span>
</code></pre>
<hr>
<span id="b3_solo_h2_19"></span><h2><a href="#总结" id="总结"></a>总结</h2>
<p style="max-width: 380px;">9个Docker最佳实践：</p>
<ol>
<li><strong>使用官方镜像</strong> - 安全可靠</li>
<li><strong>指定具体版本</strong> - 避免意外</li>
<li><strong>多阶段构建</strong> - 减小体积</li>
<li><strong>使用.dockerignore</strong> - 加速构建</li>
<li><strong>最小权限用户</strong> - 提升安全</li>
<li><strong>环境变量配置</strong> - 灵活部署</li>
<li><strong>优化缓存利用</strong> - 提升效率</li>
<li><strong>给镜像打标签</strong> - 方便管理</li>
<li><strong>扫描镜像漏洞</strong> - 安全最后一道防线</li>
</ol>
<p style="max-width: 380px;">Docker用得好是神器，用不好是灾难。遵循这些最佳实践，让你的容器化之路更顺畅。</p>
</em></em>
                                <div>
                                    <img src="https://qn.jishijun.cn/img/pub/20240925/08/0809483dnha.png" alt="善忘技术夹-公众号" width="300">
                                </div>
                        </div>

                        <footer class="tags">
                                <a class="tag" rel="tag" href="https://www.swjsj.com/tags/%E5%96%84%E7%94%A8%E4%BD%B3%E8%BD%AF">
                                    善用佳软</a>


                            <div class="rel fn-clear">
                                    <a href="https://www.swjsj.com/articles/2026/01/26/1769434659664.html" rel="prev" class="fn-left tooltipped tooltipped-n" aria-label="用React写视频?我试了一下Remotion">
                                        旧一篇
                                    </a>
                                    <a href="https://www.swjsj.com/articles/2026/01/27/1769527639069.html" rel="next" class="fn-right tooltipped tooltipped-n" aria-label="正好我也有macmini，clawd.bot终于安装好了，发现这不是很早以前用微信接入chatgpt一回事吗？为什么这个项目就突然火了">
                                        新一篇
                                    </a>
                            </div>
                        </footer>
<header class="title"><h2>评论</h2></header>
<ul class="comments" id="comments">
</ul>
    <header class="title"><h2>发表评论</h2></header>
        <table id="commentForm" class="form">
            <tbody>
                <tr>
                    <td>
                        <input placeholder="姓名" type="text" class="normalInput" id="commentName">
                    </td>
                </tr>
                <tr>
                    <td>
                        <input placeholder="邮箱" type="email" class="normalInput" id="commentEmail">
                    </td>
                </tr>
                <tr>
                    <td>
                        <input placeholder="URL" type="url" id="commentURL">
                    </td>
                </tr>
                <tr>
                    <td id="emotions" class="emotions">
                        <span class="em00" title=":smile:"></span>
                        <span class="em01" title=":joy:"></span>
                        <span class="em02" title=":stuck_out_tongue_winking_eye:"></span>
                        <span class="em03" title=":persevere:"></span>
                        <span class="em04" title=":sob:"></span>
                        <span class="em05" title=":cold_sweat:"></span>
                        <span class="em06" title=":rage:"></span>
                        <span class="em07" title=":triumph:"></span>
                        <span class="em08" title=":eyes:"></span>
                        <span class="em09" title=":scream:"></span>
                        <span class="em10" title=":sunglasses:"></span>
                        <span class="em11" title=":yum:"></span>
                        <span class="em12" title=":heart:"></span>
                        <span class="em13" title=":broken_heart:"></span>
                        <span class="em14" title=":smiling_imp:"></span>
                    </td>
                </tr>
                <tr>
                    <td>
                        <textarea rows="5" cols="96" id="comment"></textarea>
                    </td>
                </tr>
                <tr>
                    <td>
                        <input style="width:50%" placeholder="验证码" type="text" class="normalInput" id="commentValidate">
                        <img class="captcha" id="captcha" alt="validate" src="https://www.swjsj.com/captcha.do">
                    </td>
                </tr>
                <tr>
                    <td colspan="2" align="right">
                        <span class="error-msg" id="commentErrorTip"></span>
                        <button id="submitCommentButton" onclick="page.submitComment();">提交评论</button>
                    </td>
                </tr>
            </tbody>
        </table>
                        
                        <div id="relevantArticles" class="list"><h4>相关阅读</h4><ul class="marginLeft12"><li><a rel="nofollow" title="发现一款宝藏在线压缩工具：图片、视频、PDF全搞定，免费免安装" href="https://www.swjsj.com/articles/2026/02/01/1769938549285.html">发现一款宝藏在线压缩工具：图片、视频、PDF全搞定，免费免安装</a></li><li><a rel="nofollow" title="正好我也有macmini，clawd.bot终于安装好了，发现这不是很早以前用微信接入chatgpt一回事吗？为什么这个项目就突然火了" href="https://www.swjsj.com/articles/2026/01/27/1769527639069.html">正好我也有macmini，clawd.bot终于安装好了，发现这不是很早以前用微信接入chatgpt一回事吗？为什么这个项目就突然火了</a></li><li><a rel="nofollow" title="用React写视频?我试了一下Remotion" href="https://www.swjsj.com/articles/2026/01/26/1769434659664.html">用React写视频?我试了一下Remotion</a></li><li><a rel="nofollow" title="Pixelle-Video：AI驱动的视频处理工具" href="https://www.swjsj.com/articles/2026/01/25/1769335013390.html">Pixelle-Video：AI驱动的视频处理工具</a></li></ul></div>
                        <div id="randomArticles" class="list"><h4>随机阅读：</h4><ul class="marginLeft12"><li><a rel="nofollow" title="wojiaolwl = sb ID" href="https://www.swjsj.com/articles/2010/08/10/1502088832678.html">wojiaolwl = sb ID</a></li><li><a rel="nofollow" title="别怕我伤心" href="https://www.swjsj.com/articles/2010/08/10/1502088832932.html">别怕我伤心</a></li><li><a rel="nofollow" title="心情有点郁闷，不知道怎么说好" href="https://www.swjsj.com/articles/2010/08/11/1502088833121.html">心情有点郁闷，不知道怎么说好</a></li><li><a rel="nofollow" title="用电子邮件发表WordPress日志" href="https://www.swjsj.com/articles/2010/08/12/1502088833334.html">用电子邮件发表WordPress日志</a></li><li><a rel="nofollow" title="Fw: 通过电子邮件发布日志" href="https://www.swjsj.com/articles/2010/08/12/1502088833533.html">Fw: 通过电子邮件发布日志</a></li></ul></div>
                    </article>
                </main>
<aside>
    <section>
                    <div class="ad content-reset">
                
            </div>

            <div class="module">
                <header><h2>分类</h2></header>
                <main>
                        <a href="https://www.swjsj.com/category/善用佳软" aria-label="1 个标签" class="tag tooltipped tooltipped-n">
                                善用佳软</a>
                </main>
            </div>

            <div class="module">
                <header><h2>标签</h2></header>
                <main>
                        <a rel="tag" href="https://www.swjsj.com/tags/" class="tag tooltipped tooltipped-n" aria-label="509 篇文章">
                                </a>
                        <a rel="tag" href="https://www.swjsj.com/tags/cxf" class="tag tooltipped tooltipped-n" aria-label="1 篇文章">
                                cxf</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/srping" class="tag tooltipped tooltipped-n" aria-label="1 篇文章">
                                srping</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/x509" class="tag tooltipped tooltipped-n" aria-label="1 篇文章">
                                x509</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E5%B7%A5%E4%BD%9C" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                工作</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E5%BD%95%E5%B1%8F" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                录屏</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E6%AF%8F%E6%97%A5%E7%BC%96%E7%A8%8B%E5%B0%8F%E7%9F%A5%E8%AF%86" class="tag tooltipped tooltipped-n" aria-label="5 篇文章">
                                每日编程小知识</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E6%89%B9%E5%A4%84%E7%90%86" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                批处理</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD" class="tag tooltipped tooltipped-n" aria-label="8 篇文章">
                                人工智能</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E5%96%84%E7%94%A8%E4%BD%B3%E8%BD%AF" class="tag tooltipped tooltipped-n" aria-label="244 篇文章">
                                善用佳软</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F" class="tag tooltipped tooltipped-n" aria-label="6 篇文章">
                                设计模式</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E7%94%9F%E6%B4%BB" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                生活</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E6%90%9C%E7%B4%A2" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                搜索</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E5%9B%BE%E6%A0%87" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                图标</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E5%9B%BE%E7%89%87%E7%BC%96%E8%BE%91" class="tag tooltipped tooltipped-n" aria-label="4 篇文章">
                                图片编辑</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E7%BD%91%E5%9D%80" class="tag tooltipped tooltipped-n" aria-label="4 篇文章">
                                网址</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E4%BA%91%E4%B8%BB%E6%9C%BA" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                云主机</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E6%B3%A8%E5%86%8C" class="tag tooltipped tooltipped-n" aria-label="2 篇文章">
                                注册</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB" class="tag tooltipped tooltipped-n" aria-label="16 篇文章">
                                资源共享</a>
                        <a rel="tag" href="https://www.swjsj.com/tags/%E6%B5%8F%E8%A7%88%E5%99%A8" class="tag tooltipped tooltipped-n" aria-label="6 篇文章">
                                浏览器</a>
                </main>
            </div>

        <div class="module meta">
            <header>
                <h2>sily</h2>
            </header>
            <main class="fn-clear">
                <img src="https://secure.gravatar.com/avatar/d0005ead47ef756d4df290a2c0b22d3b?s=128" aria-label="sily">
                <div class="fn-right">
                    <a href="https://www.swjsj.com/archives.html">
                        785
                        <span class="ft-gray">文章</span></a><br>
                    <a href="https://www.swjsj.com/dynamic.html">
                        12
                        <span class="ft-gray">评论</span></a><br>
                    2,922,913 <span class="ft-gray">浏览</span><br>
                    48 <span class="ft-gray">访客</span>
                </div>
            </main>
        </div>

            <div class="module">
                <header><h2>评论最多的文章</h2></header>
                <main class="list">
                    <ul>
                            <li>
                                <a rel="nofollow" aria-label="4 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2024/10/19/1729339771096.html">
                                    微信公众号文章批量导出神器：还原你的阅读世界！
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="1 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2025/11/02/1762095104801.html">
                                    社交媒体数据“偷懒神器”：一键采集B站/抖音/YouTube，AI分析零门槛
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="1 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2025/09/16/1758026312223.html">
                                    告别传统“堡垒”！这款国产开源神器，让你的数字资产管理又美又安全！
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="1 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2025/07/19/1752927057429.html">
                                    GoodGYM：AI 赋能，居家健身迈入精准高效新时代！
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="1 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2025/07/14/1752499632391.html">
                                    MediaCrawler：一键爬取全网主流平台数据的神器
                                </a>
                            </li>
                    </ul>
                </main>
            </div>

            <div class="module">
                <header><h2>访问最多的文章</h2></header>
                <main class="list">
                    <ul>
                            <li>
                                <a rel="nofollow" aria-label="0 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2024/09/18/1726653760387.html">
                                    九款高效本地文件搜索工具：从文件名到全文检索的最佳选择
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="0 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2024/10/29/1730166285729.html">
                                    Windows 系统优化神器：WinUtil 让你的电脑焕发新生
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="0 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2017/11/16/1510824496958.html">
                                    nginx server_name配置通配符
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="0 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2017/11/16/1510823998827.html">
                                    百度地图选中一个不规则的区域，并根据坐标来显示
                                </a>
                            </li>
                            <li>
                                <a rel="nofollow" aria-label="0 评论" class="tooltipped tooltipped-e" href="https://www.swjsj.com/articles/2011/12/06/1502088985069.html">
                                    fastboot 救砖。恢复出厂设置。fire砖头得救了。
                                </a>
                            </li>
                    </ul>
                </main>
            </div>
    </section>
</aside>            </div>
        </div>
<footer class="footer fn-clear">
    © 2026
    版权所有@善忘技术夹 <a href="https://beian.miit.gov.cn/" target="_blank">京ICP备14054178号-1</a>
    <a href="https://www.swjsj.com">善忘技术夹</a>  &nbsp;   • &nbsp;
    <a href="https://hacpai.com/tag/solo" target="_blank">Solo</a> 2.2.0  <br>

    Powered by <a href="http://b3log.org" target="_blank">B3log</a> 开源 &nbsp;
    <span class="ft-warn">♥</span>
    Theme by <a href="https://github.com/9IPHP/9IPHP" target="_blank">9IPHP</a> &amp; <a href="http://vanessa.b3log.org" target="_blank">Vanessa</a>
</footer>
<div class="icon-up" onclick="Util.goTop()" style="display: none;"></div>

<script type="text/javascript" src="https://www.swjsj.com/js/lib/jquery/jquery.min.js" charset="utf-8"></script>
<script type="text/javascript" src="https://www.swjsj.com/js/common.min.js?1740151434577" charset="utf-8"></script>
<script type="text/javascript" src="https://www.swjsj.com/skins/9IPHP/js/common.min.js?1740151434577" charset="utf-8"></script>
<script type="text/javascript">
    var latkeConfig = {
        "servePath": "https://www.swjsj.com",
        "staticServePath": "https://www.swjsj.com",
        "isLoggedIn": "false",
        "userName": ""
    };

    var Label = {
        "skinDirName": "9IPHP",
        "em00Label": ":smile:",
        "em01Label": ":joy:",
        "em02Label": ":stuck_out_tongue_winking_eye:",
        "em03Label": ":persevere:",
        "em04Label": ":sob:",
        "em05Label": ":cold_sweat:",
        "em06Label": ":rage:",
        "em07Label": ":triumph:",
        "em08Label": ":eyes:",
        "em09Label": ":scream:",
        "em10Label": ":sunglasses:",
        "em11Label": ":yum:",
        "em12Label": ":heart:",
        "em13Label": ":broken_heart:",
        "em14Label": ":smiling_imp:"
    };
</script>
<script type="text/javascript">
    (function () {
        var $groups =  $("a[rel=group]"),
        $fancybox = $(".fancybox");
        if ($groups.length > 0 || $fancybox.length > 0) {
            if (document.createStyleSheet) {
                document.createStyleSheet("https://www.swjsj.com/plugins/fancybox/js/jquery.fancybox.css");
            } else {
                $("head").append($("<link rel='stylesheet' href='https://www.swjsj.com/plugins/fancybox/js/jquery.fancybox.css' type='text/css' charset='utf-8' />"));
            } 
            
            $.ajax({
                url: "https://www.swjsj.com/plugins/fancybox/js/jquery.fancybox.pack.js",
                dataType: "script",
                cache: true,
                complete: function() {
                    $groups.fancybox({
                        openEffect  : 'none',
                        closeEffect : 'none',
                        prevEffect : 'none',
                        nextEffect : 'none'
                    });
                    $fancybox.fancybox({
                        openEffect  : 'none',
                        closeEffect : 'none',
                        prevEffect : 'none',
                        nextEffect : 'none'
                    });
                }
            });
        }
    })();
</script>

<script type="text/javascript" src="https://www.swjsj.com/js/page.min.js?1740151434577" charset="utf-8"></script>
<script type="text/javascript">
                        var page = new Page({
                            "nameTooLongLabel": "姓名只能为 2 到 20 个字符！",
                            "mailCannotEmptyLabel": "邮箱不能为空！",
                            "mailInvalidLabel": "邮箱格式不正确！",
                            "commentContentCannotEmptyLabel": "评论内容只能为 2 到 500 个字符！",
                            "captchaCannotEmptyLabel": "验证码不能为空！",
                            "loadingLabel": "载入中....",
                            "oId": "1769435860984",
                            "skinDirName": "9IPHP",
                            "blogHost": "www.swjsj.com:80",
                            "randomArticles1Label": "随机阅读：",
                            "externalRelevantArticles1Label": "站外相关阅读："
                        });
                        var replyTo = function (id) {
                            var commentFormHTML = "<table class='form comment-reply' id='replyForm'>";
                            page.addReplyForm(id, commentFormHTML);
                        };
                        (function () {
                            page.load();
                            Skin.initArticle("文章目录", "站点概要");
                            // emotions
                            page.replaceCommentsEm("#comments .content-reset");
        page.tips.externalRelevantArticlesDisplayCount = "5";
        page.loadRandomArticles();
        page.loadExternalRelevantArticles("善用佳软"
            , "<header class='title'><h2>站外相关阅读</h2></header>");
        page.loadRelevantArticles('1769435860984', '<h4>相关阅读</h4>');
                        })();
</script>
    

<!-- Generated by B3log Latke(156 ms), 2026/06/03 23:54:27 --></body></html>
