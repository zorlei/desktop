<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【终极隐私】阅后即焚隔离沙盒部署指南 - 拒绝无痕模式</title>
    <style>
        :root {
            --bg-color: #0d1117;
            --text-color: #c9d1d9;
            --primary-color: #58a6ff;
            --code-bg: #161b22;
            --accent-green: #3fb950;
            --accent-red: #f85149;
        }
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px 20px 60px;
        }
        h1 {
            color: #fff;
            font-size: 1.8em;
            border-bottom: 2px solid #30363d;
            padding-bottom: 15px;
            margin-top: 40px;
        }
        h2 {
            color: var(--primary-color);
            font-size: 1.4em;
            margin-top: 40px;
        }
        h3 {
            color: var(--accent-green);
        }
        p {
            margin: 16px 0;
        }
        pre {
            background-color: var(--code-bg);
            padding: 16px;
            border-radius: 6px;
            overflow-x: auto;
            border: 1px solid #30363d;
        }
        code {
            font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, "Liberation Mono", monospace;
            color: #ff7b72;
            font-size: 0.9em;
        }
        pre code {
            color: #e6edf3;
            font-size: 0.85em;
        }
        .highlight {
            background-color: #21262d;
            padding: 2px 6px;
            border-radius: 4px;
            color: #79c0ff;
        }
        .warning {
            border-left: 4px solid var(--accent-red);
            background-color: rgba(248, 81, 73, 0.1);
            padding: 12px 16px;
            margin: 20px 0;
            border-radius: 0 6px 6px 0;
        }
        .tip {
            border-left: 4px solid var(--accent-green);
            background-color: rgba(63, 185, 80, 0.1);
            padding: 12px 16px;
            margin: 20px 0;
            border-radius: 0 6px 6px 0;
        }
        hr {
            border: 0;
            height: 1px;
            background: #30363d;
            margin: 40px 0;
        }
    </style>
</head>
<body>

    <h1>【终极隐私】阅后即焚隔离沙盒部署指南</h1>
    
    <p>别跟我提什么“无痕模式”，那只是骗骗家里人的小把戏。你的运营商、路由器、网站的底层追踪器，早把你的底裤看穿了。</p>
    <p>今天直接上干货。教你利用巨头的云端服务器，白嫖一台<strong>“阅后即焚”</strong>的终极隐私沙盒。用完即毁，物理断电，网警拿走硬盘都扫不出你刚才看了什么。</p>
    <p>不需要懂代码，跟着下面的步骤，直接复制粘贴。</p>

    <hr>

    <h2>Step 1: 部署 2026 Kasm 核心引擎</h2>
    <p>打开你的 GitHub Codespaces 终端（那个黑框框）。根据你的口味，我准备了三个版本的“召唤咒语”。选一个你喜欢的，复制，粘贴，回车。</p>

    <h3>版本A：单应用浏览器（最轻量，纯粹为了冲浪）</h3>
    <pre><code>sudo docker run -d --rm --name my-sandbox -p 6901:6901 --shm-size=512m -e VNC_PW=888888 kasmweb/chrome:1.15.0</code></pre>
    <p class="tip">关机/自毁指令：<code>sudo docker stop my-sandbox</code></p>

    <h3>版本B：极简科技风（完整的 Ubuntu 桌面，小白最爱，强烈推荐！）</h3>
    <pre><code>sudo docker run -d --rm --name my-desktop -p 6901:6901 --shm-size=512m -e VNC_PW=888888 kasmweb/ubuntu-jammy-desktop:1.15.0</code></pre>
    <p class="tip">关机/自毁指令：<code>sudo docker stop my-desktop</code></p>

    <h3>版本C：极致黑客风（自带无数渗透工具的 Kali Linux）</h3>
    <pre><code>sudo docker run -d --rm --name my-hacker-desktop -p 6901:6901 --shm-size=512m -e VNC_PW=888888 kasmweb/kali-rolling-desktop:1.15.0</code></pre>
    <p class="tip">关机/自毁指令：<code>sudo docker stop my-hacker-desktop</code></p>

    <hr>

    <h2>Step 2: 登录你的赛博分身</h2>
    <p>在端口列表中把 <code>6901</code> 改为 <strong>Public（公开）</strong>，协议强行改为 <strong>HTTPS</strong>，然后点击链接进入。忽略那个吓人的红色安全警告（点击继续访问）。</p>
    <ul>
        <li>Username（用户名）输入： <span class="highlight">kasm_user</span></li>
        <li>Password（密码）输入： <span class="highlight">888888</span></li>
    </ul>

    <hr>

    <h2>Step 3: 注入“中文灵魂”（两步汉化法）</h2>
    <p>默认全是英文看不懂？别去系统设置里找了，没用的。真正的极客直接用代码改底层血液。如果你选了 Ubuntu 桌面，跟着做：</p>
    <p><strong>第一步：回到 GitHub Codespaces 的黑框框，先杀掉当前的英文桌面：</strong></p>
    <pre><code>sudo docker stop my-desktop</code></pre>
    <p><strong>第二步：输入带有中文环境变量的终极召唤指令：</strong></p>
    <pre><code>sudo docker run -d --rm --name my-desktop -p 6901:6901 --shm-size=512m -e VNC_PW=888888 -e LC_ALL=zh_CN.UTF-8 -e LANG=zh_CN.UTF-8 -e LANGUAGE=zh_CN.UTF-8 kasmweb/ubuntu-jammy-desktop:1.15.0</code></pre>
    <p>再次进入网页，你会发现整个系统已经变成了完美的简体中文。</p>

    <hr>

    <h2>Step 4: 红蓝药丸的抉择（进阶玩法）</h2>
    <div class="warning">
        <strong>注意：</strong>上面代码里的 <code>--rm</code> 是一个自毁程序。这意味着你只要关机（stop），里面的数据、浏览记录瞬间全部物理抹除。这是绝对的隐私，但也意味着你每次开机都是个空系统。
    </div>

    <p><strong>如果不想要“阅后即焚”，只想白嫖一台能“关机/开机”保存数据的云电脑怎么办？</strong></p>
    <p>很简单，把 <code>--rm</code> 这四个字符删掉！用下面这段代码启动：</p>
    <pre><code>sudo docker run -d --name my-desktop -p 6901:6901 --shm-size=512m -e VNC_PW=888888 -e LC_ALL=zh_CN.UTF-8 -e LANG=zh_CN.UTF-8 -e LANGUAGE=zh_CN.UTF-8 kasmweb/ubuntu-jammy-desktop:1.15.0</code></pre>
    
    <p><strong>此时的关机（不再销毁）：</strong></p>
    <p>当你输入 <code>sudo docker stop my-desktop</code> 时，它只是正常关机休眠。你存的文件、没关的网页，全都在！</p>
    
    <p><strong>如何再次开机（唤醒）：</strong></p>
    <p>明天睡醒想接着玩？不需要再敲长代码了，只需输入这句：</p>
    <pre><code>sudo docker start my-desktop</code></pre>
    <p>瞬间秒开，一切如初。</p>

    <hr>
    <p style="text-align: center; color: #8b949e; font-size: 0.9em;">Stay hidden. 保持隐蔽，别干坏事。</p>

</body>
</html>
