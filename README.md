# Sway

![sway](https://github.com/xuxiaodong/swaywmconf/raw/master/screenshot.png)

[Sway](https://swaywm.org/) 运行在 [Wayland](https://wayland.freedesktop.org/) 上，并提供与 [i3](https://i3wm.org/) 窗口管理器一致的使用体验。我之前使用 [Windowchef](https://github.com/tudurom/windowchef)，在连续试用 Sway 近一周后，决定将其作为主力桌面环境的关键组件。

## 转换的组件

在一个可以工作的桌面环境中包含一些必须的组件，下列组件已经转换：

| 功能     | 之前                 | 现在              |
| -------- | -------------------- | ----------------- |
| 窗口管理 | Windowchef           | Sway              |
| 双显管理 | xrandr               | Sway 内置         |
| 交换按键 | setxkbmap            | Sway 内置         |
| 设置壁纸 | hsetroot             | Sway 内置         |
| 热键管理 | sxhkd                | Sway 内置         |
| 锁屏     | slock                | swayidle/swaylock |
| 状态栏   | 自制脚本             | Waybar            |
| 通知     | dunst                | mako              |
| 截图     | import               | grim              |
| 录屏     | SimpleScreenRecorder | wf-recorder       |

## 不必转换的组件

以下组件为通用组件，不必进行转换：

* 输入法：Fcitx
* 终端模拟器：rxvt-unicode
* 终端多路复用器：tmux
* 应用启动器：rofi

## 配置管理

Sway 及其配件的配置通过 [GNU Stow](https://www.gnu.org/software/stow/) 进行管理，可按如下方式设置：

```bash
git clone https://github.com/xuxiaodong/swaywmconf.git ~/.dotfiles
cd ~/.dotfiles
stow sway waybar urxvt rofi
```

## 按键绑定

基本采用 Sway 默认按键绑定，额外需求为自行定制。$mod 变量使用徽标键作为修饰键，$left/$down/$up/$right 使用 Vim 风格的方向键，即 `hjkl`。

### 基本

| 按键          | 作用           |
| ------------- | -------------- |
| $mod+Return   | 启动终端       |
| $mod+Shift+q  | 关闭聚焦的窗口 |
| $mod+鼠标左键 | 拖动浮动窗口   |
| $mod+鼠标右键 | 调整窗口大小   |
| $mod+Shift+c  | 重载配置       |
| $mod+Shift+e  | 退出 Sway      |

### 移动

| 按键                                  | 作用                               |
| ------------------------------------- | ---------------------------------- |
| $mod+$left 或 $mod+Left               | 移动聚焦（左）                     |
| $mod+$down 或 $mod+Down               | 移动聚焦（下）                     |
| $mod+$up 或 $mod+Up                   | 移动聚焦（上）                     |
| $mod+$right 或 $mod+Right             | 移动聚焦（右）                     |
| $mod+Shift+$left 或 $mod+Shift+Left   | 移动聚焦的窗口（左）               |
| $mod+Shift+$down 或 $mod+Shift+Down   | 移动聚焦的窗口（下）               |
| $mod+Shift+$up 或 $mod+Shift+Up       | 移动聚焦的窗口（上）               |
| $mod+Shift+$right 或 $mod+Shift+Right | 移动聚焦的窗口（右）               |
| $mod+y                                | 移动聚焦的窗口（浮动模式：左上角） |
| $mod+m                                | 移动聚焦的窗口（浮动模式：中央）   |

### 工作区

| 按键         | 作用                      |
| ------------ | ------------------------- |
| $mod+1       | 切换到工作区 1            |
| $mod+2       | 切换到工作区 2            |
| ...          | ...                       |
| $mod+0       | 切换到工作区 10           |
| $mod+Shift+1 | 移动聚焦的容器到工作区 1  |
| $mod+Shift+2 | 移动聚焦的容器到工作区 2  |
| ...          | ...                       |
| $mod+Shift+0 | 移动聚焦的容器到工作区 10 |

### 布局

| 按键             | 作用                          |
| ---------------- | ----------------------------- |
| $mod+b           | 水平分屏                      |
| $mod+v           | 垂直分屏                      |
| $mod+s           | 切换到 stacking（堆叠）式布局 |
| $mod+w           | 切换到 tabbed（标签页）式布局 |
| $mod+e           | 切换到 split（分割）式布局    |
| $mod+f           | 切换到全屏                    |
| $mod+Shift+space | 在平铺和浮动模式之间切换      |
| $mod+space       | 在平铺和浮动区域之间交换聚焦  |
| $mod+a           | 移动聚焦到父容器              |

### 暂存器

暂存器可以隐藏窗口。

| 按键             | 作用                   |
| ---------------- | ---------------------- |
| $mod+Shift+minus | 移动聚焦的窗口到暂存器 |
| $mod+minus       | 显示隐藏的暂存窗口     |

### 调整窗口大小

| 按键            | 作用                    |
| --------------- | ----------------------- |
| $mod+r          | 进入调整模式            |
| $left 或 Left   | 缩小容器宽度            |
| $down 或 Down   | 放大容器高度            |
| $up 或 Up       | 缩小容器高度            |
| $right 或 Right | 放大容器宽度            |
| $mod+n          | 重新调整窗口到 1280x720 |

### 其它

| 按键                            | 作用      |
| ------------------------------- | --------- |
| $mod+c                          | 锁屏      |
| $mod+t                          | 启动 tmux |
| Print/Shift+Print/Control+Print | 截图      |

建议阅读 Sway config 来了解输入、输出、状态栏、自启动程序等其它配置，我注释很详细。

## 兼容应用

我日常使用的应用其兼容性如下：

| 名称        | 结果     |
| ----------- | -------- |
| Audacity    | 偶有崩溃 |
| Calibre     | 好       |
| Chromium    | 好 *     |
| digiKam     | 好       |
| Firefox     | 好       |
| GIMP        | 好       |
| Inkscape    | 好       |
| Kdenlive    | 闪烁     |
| KeePassXC   | 好       |
| Krita       | 好       |
| LibreOffice | 好       |
| Olive       | 好       |
| VSCodium    | 好 *     |
| Zathura     | 好       |
| Zeal        | 好       |

*：这些程序需使用 `GDK_BACKEND=x11` 环境变量启动。