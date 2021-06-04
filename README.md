# MacOS常用软件和配置

## 首先

**先安装Xcode**

1. 先用离线安装包安装一个代理软件（例如trojanx），配置代理，安装[brew](https://brew.sh/)
2. `echo 'export PATH="/usr/local/sbin:$PATH"' > $ZSH_CUSTOM/brew.zsh`
3. `brew doctor`，出现问题就修复
4. 安装cask，`brew tap homebrew/cask`
5. 使用brew安装一个代理软件（例如qv2ray），卸载离线安装的代理软件，重新配置代理
6. `echo "alias setproxy='export HTTP_PROXY=http://127.0.0.1:1081 export HTTPS_PROXY=http://127.0.0.1:1081 export ALL_PROXY=socks5://127.0.0.1:1080 export NO_PROXY=localhost,127.0.0.0/8,192.168.1.0/8'" >> $ZSH_CUSTOM/alias.zsh`
7. `echo "alias unsetproxy='unset HTTP_PROXY HTTPS_PROXY ALL_PROXY NO_PROXY'" >> $ZSH_CUSTOM/alias.zsh`

---

## brew tap

本地仓库目录/usr/local/Homebrew/Library/Taps/

| 名称                    | 用途             | 备注                                                                                              |
| ---------------------- | --------------- | ------------------------------------------------------------------------------------------------- |
| homebrew/cask-fonts    | 字体             | 目录<br>homebrew/homebrew-cask-fonts/Casks                                                        |
| homebrew/services      | 管理服务          | `brew services --help`                                                                           |
| homebrew/cask-versions | 安装cask的历史版本 | 目录<br>homebrew/homebrew-cask-versions/Casks<br>命令<br>`brew install homebrew/cask-versions/xxx` |
| beeftornado/rmtree     | 卸载formula和依赖 | `brew rmtree xxx`                                                                                 |
| buo/cask-upgrade       | 升级cask         | `brew cu -fa`                                                                                     |
| ringohub/redis-cli     | redis-cli       | `brew install redis-cli`                                                                          |
| xuelingkang/taps       | 安装自己维护的工具 | `brew install java8`                                                                              |

---

## brew 常用软件

Formulae

`coreutils frpc git gnu-sed gnupg maven mysql-client neofetch node openvpn p7zip python@3.9 tree vim wget`

Casks

`alfred appcleaner baidunetdisk datagrip docker drawio google-chrome intellij-idea iterm2 maciasl oss-browser postman soundflower thunderbird typora visual-studio-code vlc webstorm`

---

## vimplus

```shell
git clone https://github.com/chxuan/vimplus.git ~/.vimplus
cd ~/.vimplus
./install.sh
# 禁用YouCompleteMe插件，比较碍事，且crontab -e命令报错
echo "UnPlug 'YouCompleteMe'" >> ~/.vimrc.custom.plugins
```

---

## iterm2

```shell
brew install iterm2
```

### 取消关闭时的警告

![preferences-general-closing](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/preferences-general-closing.png)

### 关闭自动更新

![preferences-general-services](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/preferences-general-services.png)

### 取消选中时复制

![preferences-general-selection](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/preferences-general-selection.png)

### 使用最小主题，status bar放在底部

![preferences-appearance-general](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/preferences-appearance-general.png)

### 增加或减少标签页时保持窗口大小

![preferences-appearance-tabs](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/preferences-appearance-tabs.png)

### 非激活状态调暗

![preferences-appearance-dimming](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/preferences-appearance-dimming.png)

### 配置字体

![profiles-text](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/profiles-text.png)

### 关闭鼠标定位光标

![profiles-terminal](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/profiles-terminal.png)

### 启用status bar

![profiles-session](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/profiles-session.png)

### 配置status bar

![profiles-session-status-bar](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/profiles-session-status-bar.png)

### status bar高级选项，配置字体

![profiles-session-status-bar-advance](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/profiles-session-status-bar-advance.png)

### 配置快捷键，自然文本编辑

![profiles-keys](https://raw.githubusercontent.com/xuelingkang/assets/master/macos-settings/iterm2/profiles-keys.png)

### 导入Dracula配色方案

```shell
git clone https://github.com/dracula/iterm.git /path/to/local/folder
```

iterm首选项导入**Dracula.itermcolors**，然后切换到该方案

`Preferences -> Profiles -> Colors -> Color Presets`

---

## oh-my-zsh

```shell
# curl 安装
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# wget 安装
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

### spaceship主题

```shell
# 克隆主题仓库
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
# 软连接到自定义主题目录
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
# 设置环境变量
echo 'export ZSH_THEME="spaceship"' > $ZSH_CUSTOM/theme.zsh
```

### 语法高亮插件

```shell
# 使用brew安装插件
brew install zsh-syntax-highlighting
# 软连接到custom目录
ln -s /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh $ZSH_CUSTOM/zsh-syntax-highlighting.zsh
```

---

## Finder显示完整路径

`显示 -> 显示路径栏` 或使用快捷键 `option+command+p`

在Finder窗口底部显示可交互的路径栏

---

## 使用brew安装java8

先去[oracle java8下载页面](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)，下载java8安装包，保存到下载目录

```shell
brew tap xuelingkang/taps
brew install java8
echo 'export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_291.jdk/Contents/Home' > $ZSH_CUSTOM/java.zsh
echo 'export CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.' >> $ZSH_CUSTOM/java.zsh
```

---

## 使用brew安装maven

```shell
brew install maven
brew uninstall --ignore-dependencies openjdk
echo 'export M2_HOME=/usr/local/Cellar/maven/3.8.1/libexec' > $ZSH_CUSTOM/maven.zsh
echo 'export MAVEN_HOME=/usr/local/Cellar/maven/3.8.1/libexec' >> $ZSH_CUSTOM/maven.zsh
echo 'export MAVEN_REPOSITORY=$HOME/.m2/repository' >> $ZSH_CUSTOM/maven.zsh
```

---

## thunderbird

可以设置网络代理，方便配置gmail

### 缩放大小

`首选项 -> 常规（滚动到底部） -> 配置编辑器 -> 搜索"pixels"`

修改"layout.css.devPixelsPerPx"，保存即生效

### 设置默认排序

`首选项 -> 常规（滚动到底部） -> 配置编辑器 -> 搜索"mailnews.default"`

搜索结果

```
Preference Name                      Status       Type        Value
mailnews.default_news_sort_order     default      integer     x
mailnews.default_news_sort_type      default      integer     y
mailnews.default_sort_order          default      integer     x
mailnews.default_sort_type           default      integer     y
```

x
```
1 = Ascending
2 = Descending
```

y
```
17 = None
18 = Date
19 = Subject
20 = Author
21 = ID (Order Received)
22 = Thread
23 = Priority
24 = Status
25 = Size
26 = Flagged
27 = Unread
28 = Recipient
29 = Location
30 = Label
31 = Junk Status
32 = Attachments
33 = Account
34 = Custom
35 = Received
```

修改成**按照时间倒序排列**

x=2
y=18

