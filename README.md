最近有人给我推荐了个代理软件，查了下发现是专门为 Telegram 开发的代理软件，代理服务端限制了客户端只允许访问 Telegram 的服务器。

相比于使用其他代理软件，然后 Telegram 配置链接本地代理软件而言，该方法更方便一些，无需每次启动 Telegram 都需要先启动代理软件，特别是对于手机使用者来说。

至于该软件的特性，大概就是占用资源少、使用方便、Telegram官方支持（是不是官方开发的我也不知道，估计不是）。

注意：MTProxy 仅支持 Telegram 客户端使用，无法用于代理其他网站和软件！

Github 项目地址：https://github.com/TelegramMessenger/MTProxy

系统要求
CentOS 7 / Debian 7+ / Ubuntu 14.04 +

推荐 Debian 7/8 x64，这个是我一直使用的系统，我的脚本在这个系统上面出错率最低。

注意：因为 CentOS 6 系统的 GCC 版本过低，会导致编译失败，请使用更高版本的系统！
安装步骤
# 执行下面的代码下载并运行脚本：
wget -N --no-check-certificate https://softs.loan/Bash/mtproxy.sh && chmod +x mtproxy.sh && bash mtproxy.sh
 
# 如果上面这个脚本无法下载，尝试使用备用下载：
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/mtproxy.sh && chmod +x mtproxy.sh && bash mtproxy.sh
运行脚本后会出现脚本操作菜单，选择并输入1就会开始安装。

请输入 MTProxy 端口 [1-65535]
(默认: 7000):
 
========================
    端口 :  7000
========================
 
请输入 MTProxy 密码（手动输入必须为32位，[0-9][a-z][A-Z]，建议随机生成）
(默认：随机生成):
 
========================
    密码 :  xxxxx 
========================
 
如果本机是NAT服务器（谷歌云、微软云、阿里云等），则请输入你的服务器内网IP，否则会导致无法使用。如果不是请直接回车！
(默认：回车跳过):
 
========================
    NAT :  NO
========================
 
[信息] MTProxy 停止成功 !
[信息] MTProxy 启动中...
[信息] MTProxy 启动成功 !
 
————————————————
 
 Mtproto Proxy 信息 :
 
 地址    : x.x.x.x
 端口    : 7000
 密码    : xxxxx
 伪装    : 无
 链接    : tg://proxy?server=xxxxxx...
 链接    : https://t.me/proxy?server=xxxxxx...
 
————————————————
使用说明
进入下载脚本的目录并运行脚本：./mtproxy.sh

然后选择你要执行的选项即可。

  MTProxy 一键管理脚本 [v1.0.0]
  ---- Toyo | doub.io/shell-jc7 ----
  
  0. 升级脚本
————————————
  1. 安装 MTProxy
  2. 更新 MTProxy
  3. 卸载 MTProxy
————————————
  4. 启动 MTProxy
  5. 停止 MTProxy
  6. 重启 MTProxy
————————————
  7. 设置 账号配置
  8. 查看 账号信息
  9. 查看 日志信息
 10. 查看 链接信息
————————————
 
 当前状态: 已安装 并 已启动
 
 请输入数字 [0-10]:
其他操作
启动：/etc/init.d/mtproxy start

停止：/etc/init.d/mtproxy stop

重启：/etc/init.d/mtproxy restart

查看状态：/etc/init.d/mtproxy status

安装目录：/usr/local/mtproxy

配置文件：/usr/local/mtproxy/mtproxy.conf

日志文件：/usr/local/mtproxy/mtproxy.log

Telegram 使用方法说明：
如果你的 TG 客户端没有 Mtproto 代理选项，那么请更新到最新版本！

Telegram 内置了 Mtproto 代理选项，所以TG客户端内点击 tg://proxy?xxxx... 链接就会自动配置代理，非常方便。
PC 使用步骤如下：

点击 Telegram 客户端左上角的 三横杠 按钮，

然后点击 你的头像 就会进入保存消息聊天窗口中（在这里发只会被自己看到，而且正好保存起来），

接着复制 tg://proxy?xxxx... 并发送，

最后点击 tg://proxy?xxxx... 链接后就会提示你是否要启用这个代理，点击 启用 按钮，

就会发现自动添加并使用该代理配置了。

或者你可以浏览器访问 https://t.me/proxy?server=xxxxxx... 链接，然后浏览器会自动调用 Telegram 客户端。

至于手动添加，只需要去代理设置处，添加新代理并选择 Mtproto 代理选项，根据账号信息分别填写服务器IP、端口、密码即可。

其他说明
注意：MTProxy 仅支持 Telegram 客户端使用，无法用于其他软件！
启动失败，日志提示 'S' option requires exactly 32 hex digits 错误

该问题只出现于自定义密码时，因为 MTProxy 为了安全性而要求密码必须是 32位（多了少了都不行），如果数量不对就会提示这个，建议用脚本随机生成！

提示wget: unknown host “softs.loan” 之类的错误
这是无法解析域名，多半是DNS的问题，请更换DNS为谷歌DNS(以下两行一起复制 一起执行)。

echo -e "nameserver 8.8.8.8nnameserver 8.8.4.4" > /etc/resolv.conf

提示 wget: command not found 的错误
这是你的系统精简的太干净了，wget都没有安装，所以需要安装wget。

# CentOS系统:
yum install -y wget
 
# Debian/Ubuntu系统:
apt-get install -y wget
升级脚本
升级脚本只需要重新下载脚本文件就可以了，会自动覆盖原文件。

更新日志
2018年07月01日，版本 v1.0.3

更换 安装方式为 Git。
—— 突然发现一些人编译失败的原因是因为没有安装 git ，这就蛋疼了，老实换回去用 Git 吧。
2018年07月01日，版本 v1.0.2

优化 随机密码生成（舍弃 xxd ，能少装一个软件就少装一个）。
修复 NAT设置的一个小BUG。
2018年07月01日，版本 v1.0.1

新增 NAT设置。
—— 如果是NAT服务器（如谷歌云、微软云、阿里云等），则需要填写内网IP地址，否则会导致无法连接！如果不是就直接回车跳过。
2018年07月01日，版本 v1.0.0

推出 正式版。

# MTProxy
Simple MT-Proto proxy

## Building
Install dependencies, you would need common set of tools for building from source, and development packages for `openssl` and `zlib`.

On Debian/Ubuntu:
```bash
apt install git curl build-essential libssl-dev zlib1g-dev
```
On CentOS/RHEL:
```bash
yum install openssl-devel zlib-devel
yum groupinstall "Development Tools"
```

Clone the repo:
```bash
git clone https://github.com/TelegramMessenger/MTProxy
cd MTProxy
```

To build, simply run `make`, the binary will be in `objs/bin/mtproto-proxy`:

```bash
make && cd objs/bin
```

If the build has failed, you should run `make clean` before building it again.

## Running
1. Obtain a secret, used to connect to telegram servers.
```bash
curl -s https://core.telegram.org/getProxySecret -o proxy-secret
```
2. Obtain current telegram configuration. It can change (occasionally), so we encourage you to update it once per day.
```bash
curl -s https://core.telegram.org/getProxyConfig -o proxy-multi.conf
```
3. Generate a secret to be used by users to connect to your proxy.
```bash
head -c 16 /dev/urandom | xxd -ps
```
4. Run `mtproto-proxy`:
```bash
./mtproto-proxy -u nobody -p 8888 -H 443 -S <secret> --aes-pwd proxy-secret proxy-multi.conf -M 1
```
... where:
- `nobody` is the username. `mtproto-proxy` calls `setuid()` to drop privilegies.
- `443` is the port, used by clients to connect to the proxy.
- `8888` is the local port. You can use it to get statistics from `mtproto-proxy`. Like `wget localhost:8888/stats`. You can only get this stat via loopback.
- `<secret>` is the secret generated at step 3. Also you can set multiple secrets: `-S <secret1> -S <secret2>`.
- `proxy-secret` and `proxy-multi.conf` are obtained at steps 1 and 2.
- `1` is the number of workers. You can increase the number of workers, if you have a powerful server.

Also feel free to check out other options using `mtproto-proxy --help`.

5. Generate the link with following schema: `tg://proxy?server=SERVER_NAME&port=PORT&secret=SECRET` (or let the official bot generate it for you).
6. Register your proxy with [@MTProxybot](https://t.me/MTProxybot) on Telegram.
7. Set received tag with arguments: `-P <proxy tag>`
8. Enjoy.

## Random padding
Due to some ISPs detecting MTProxy by packet sizes, random padding is
added to packets if such mode is enabled.

It's only enabled for clients which request it.

Add `dd` prefix to secret (`cafe...babe` => `ddcafe...babe`) to enable
this mode on client side.

## Systemd example configuration
1. Create systemd service file (it's standard path for the most Linux distros, but you should check it before):
```bash
nano /etc/systemd/system/MTProxy.service
```
2. Edit this basic service (especially paths and params):
```bash
[Unit]
Description=MTProxy
After=network.target

[Service]
Type=simple
WorkingDirectory=/opt/MTProxy
ExecStart=/opt/MTProxy/mtproto-proxy -u nobody -p 8888 -H 443 -S <secret> -P <proxy tag> <other params>
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
3. Reload daemons:
```bash
systemctl daemon-reload
```
4. Test fresh MTProxy service:
```bash
systemctl restart MTProxy.service
# Check status, it should be active
systemctl status MTProxy.service
```
5. Enable it, to autostart service after reboot:
```bash
systemctl enable MTProxy.service
```

## Docker image
Telegram is also providing [official Docker image](https://hub.docker.com/r/telegrammessenger/proxy/).
Note: the image is outdated.
