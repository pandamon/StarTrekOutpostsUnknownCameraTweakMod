



# STOU Camera Tweak

《星际迷航：未知前哨》（Star Trek: Outposts Unknown）镜头增强 Mod。让镜头手感回归正常 RTS 操作：WASD 平移更快，可选 Shift 冲刺，右键直接拖拽地面。

## 游戏内效果

- **WASD 平移加速**：按住 W/A/S/D 时，镜头移动速度是原版的 **4 倍**。
- **Shift 冲刺**：按住 **左 Shift** 再按 WASD，速度为原版的 **8 倍**；松开立即回落到 4 倍。按键与倍率均可配置。
- **右键拖拽地面**：按住右键抓住光标下的地面直接拖动，地面跟手移动，1 屏幕像素 = 对应世界距离（可调）。原版"鼠标偏离屏幕中心即虚拟摇杆推杆、光标不动镜头也持续漂移"的行为被彻底关闭；拖拽期间同时屏蔽屏幕边缘自动推镜。鼠标停，镜头停。
- 不修改任何玩法数值、存档或 UI，纯客户端镜头手感调整。

## 前置要求

| 项目 | 版本 |
|---|---|
| 游戏 | Steam 版，Unity 6000.3.19f1，IL2CPP x64 |
| BepInEx | **6.0.0-be.793**（IL2CPP x64 版，含 Il2CppInterop） |

游戏是 IL2CPP 打包，**BepInEx 5 不可用**。

## 安装

1. 在游戏根目录安装 BepInEx 6.0.0-be.793（IL2CPP x64），先启动一次游戏，等 `BepInEx\interop\` 与 `BepInEx\config\` 正常生成后关闭游戏。
2. 把 `StarTrekCamTweak.dll` 放入：
   ```
   <游戏根目录>\BepInEx\plugins\
   ```
3. 启动游戏，插件自动加载，首次运行会生成配置文件。

## 配置文件

生成位置：

```
<游戏根目录>\BepInEx\config\marvis.stou.camtweak.cfg
```

每次启动游戏时读取，改完需重进游戏生效。

### [WASD]

| 键 | 默认值 | 范围 | 含义 |
|---|---|---|---|
| `Enabled` | `true` | — | WASD 加速总开关 |
| `SpeedMultiplier` | `4` | 0.1 ~ 20 | 常态平移倍率。`1` = 原版速度，`4` = 四倍速 |
| `BoostEnabled` | `true` | — | 是否启用冲刺键 |
| `BoostKey` | `LeftShift` | — | 冲刺键，取 `UnityEngine.InputSystem.Key` 键名：`LeftShift`、`LeftCtrl`、`LeftAlt`、`Space`、`CapsLock` 等 |
| `BoostMultiplier` | `8` | 0.1 ~ 40 | 按住冲刺键时的倍率，**替代** `SpeedMultiplier`，不叠乘 |

### [RightDrag]

| 键 | 默认值 | 范围 | 含义 |
|---|---|---|---|
| `Enabled` | `true` | — | 是否把右键平移改为拖拽地面 |
| `GroundDistancePerPixel` | `1` | 0.05 ~ 10 | 每屏幕像素鼠标位移对应的地面世界距离。`1` = 光标下的地面 1:1 跟手；调大则同样的鼠标移动能拖得更远、更灵敏 |
| `BlockEdgeScrollWhileDragging` | `true` | — | 拖拽期间屏蔽屏幕边缘自动推镜 |
| `SmoothDrag` | `false` | — | 给拖拽加轻微平滑，手感更柔，但会牺牲严格的 1:1 跟手 |

### [Debug]

| 键 | 默认值 | 含义 |
|---|---|---|
| `VerboseLog` | `false` | 向 BepInEx 控制台输出逐帧拖拽数据与倍率切换，仅排障用，日志量大 |

把 `VerboseLog` 设为 `true` 后：按住/松开冲刺键会打印 `speed mult 4.00 -> 8.00` / `8.00 -> 4.00`；每次拖拽结束会打印 `drag end: mouse=..px ground=..u ratio=..`，可用来核对 1:1 是否准确。

*（内容由AI生成，仅供参考）*
