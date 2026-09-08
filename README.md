# @yefeng008/plugin-gantt-enhanced

NocoBase 甘特图区块插件（增强版），基于官方 [`@nocobase/plugin-gantt`](https://github.com/nocobase/nocobase/tree/main/packages/plugins/%40nocobase/plugin-gantt) fork 而来。

> A NocoBase Gantt block plugin (enhanced), forked from the official `@nocobase/plugin-gantt`.

## 增强功能 / Enhancements

相比官方甘特图，本插件新增以下功能：

### 1. 允许用户自定义缩放

- 区块配置中新增「允许用户自定义缩放」开关（默认关闭）
- 开启后，工具栏右侧出现缩放下拉框，使用用户（非配置用户）可自由切换缩放等级
- 缩放选项：小时 / 四分之一天 / 半天 / 天 / 周 / 月 / 季度 / 年

### 2. 时间导航按钮组

- 工具栏新增 3 个按钮：**左箭头 / 中间"回到当前" / 右箭头**
- 左右箭头：无限移动时间坐标轴（每次移动一个时间单位，可连续点击）
- 中间按钮：回到当前时间，文字随缩放等级智能变化：
  - 半天以内（小时/四分之一天/半天）→「现在」
  - 天 →「今天」
  - 周 →「本周」
  - 月 →「本月」
  - 季度 →「本季度」
  - 年 →「本年度」

### 3. 移除水平滚动条

用左右按钮替代水平滚动条，界面更简洁。

## 安装 / Installation

**方式 A：插件管理器上传**

1. NocoBase 管理后台 → 插件管理器 → 上传插件
2. 选择 `plugin-gantt-enhanced-2.2.0.tgz`

**方式 B：命令行**

```bash
yarn pm add ./plugin-gantt-enhanced-2.2.0.tgz
```

安装后在插件管理器中启用本插件，区块类型中会出现「甘特图（增强版）」。

> 建议禁用官方「甘特图」插件，避免两个同名区块混淆。

## 使用说明 / Usage

1. 在页面中添加「甘特图（增强版）」区块，绑定数据表
2. 配置字段映射：标题、开始日期、结束日期、进度、颜色等
3. 在区块配置中打开「允许用户自定义缩放」
4. 使用工具栏的左右按钮浏览时间轴，点击中间按钮回到当前时间

## 与官方 gantt 的关系 / Relationship with upstream

| | 官方 gantt | 本插件 |
|---|---|---|
| 包名 | `@nocobase/plugin-gantt` | `@yefeng008/plugin-gantt-enhanced` |
| 升级覆盖 | 会被 NocoBase 升级覆盖 | 独立包，不受影响 |
| 增强功能 | 无 | 缩放开关 + 时间导航 + 去滚动条 |

## 开发 / Development

```bash
# 在 NocoBase 源码环境中
yarn build @yefeng008/plugin-gantt-enhanced   # 编译
yarn tar @yefeng008/plugin-gantt-enhanced     # 打包
```

目录结构：

```
src/
├── client/        # v1 客户端（兼容旧界面）
├── client-v2/     # v2 客户端（/v/ 界面，增强功能在此实现）
│   └── models/
│       ├── GanttBlockModel.tsx       # 区块模型（缩放状态、时间导航按钮）
│       └── components/GanttBlock.tsx # 区块组件（时间窗口偏移、回到当前）
├── server/        # 服务端
└── locale/        # 多语言
```

## License

Apache-2.0（沿用上游许可证）
