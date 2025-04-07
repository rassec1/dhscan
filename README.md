# DHSCAN - 高性能Web服务扫描工具

DHSCAN 是一个用 Go 语言编写的高性能 Web 服务扫描工具，支持大规模并发扫描，可以快速发现目标主机上的 Web 服务。

## 功能特点

- 🚀 高性能并发扫描
- 🌐 支持多种输出格式 (HTML/JSON/CSV)
- 🔍 智能端口探测
- 📊 美观的 HTML 报告
- 🛡️ WAF 检测
- 💾 自动保存和断点续扫
- 📝 详细的扫描日志
- 🎯 支持多种目标输入方式（单个目标、文件列表、IP范围）
- 🔄 自动重试机制
- 📈 资源使用监控

## 安装说明

### 前置要求

- Go 1.16 或更高版本

### 安装步骤

```bash
# 克隆项目
git clone https://github.com/rassec1/dhscan.git

# 进入项目目录
cd dhscan

# 编译项目
go build -o dhscan
```

## 使用方法

### 基本用法

```bash
./dhscan -p 80,443 example.com
```

### 命令行参数

```bash
选项：
  -p string      指定端口范围 (默认 "80,443")
  -t int         超时时间(秒) (默认 5)
  -c int         并发数 (默认 1000)
  -f string      从文件读取目标
  -r string      IP范围 (CIDR格式如192.168.1.0/24 或范围如192.168.1.1-192.168.1.255)
  -rt int        重试次数 (默认 1)
  -format string 输出格式 (csv,json,html) (默认 "html")
  --ignore-status string 忽略的状态码 (默认 "400")
  --min-status int      最小状态码
  --max-status int      最大状态码
```

### 示例

```bash
# 扫描单个目标的多个端口
./dhscan -p 80,443,8080-8090 example.com

# 从文件读取目标
./dhscan -f targets.txt -p 80,443

# 扫描IP范围
./dhscan -r 192.168.1.0/24 -p 80,443

# 指定输出格式
./dhscan -format "html,json" -p 80,443 example.com

# 设置并发和超时
./dhscan -c 2000 -t 10 -p 80,443 example.com
```

## 输出格式

### HTML 报告
- 美观的 Web 界面
- 详细的统计信息
- 可过滤和搜索的结果
- 自适应布局

### JSON 格式
- 结构化数据
- 便于程序处理
- 包含完整扫描信息

### CSV 格式
- 表格形式
- 兼容 Excel
- 便于数据分析

## 性能优化

- 智能并发控制
- 内存使用监控
- 自动 GC 优化
- 批量处理机制

## 注意事项

1. 确保有足够的系统资源（内存、CPU）
2. 大规模扫描时注意调整并发数
3. 建议使用 `-rt` 参数设置重试次数
4. 扫描结果会自动保存，程序意外退出可恢复

## 许可证

[MIT](LICENSE) © rassec1


## 更新日志

### v1.0.0
- 初始版本发布
- 支持基本的 Web 服务扫描
- 多种输出格式支持
- 自动保存功能 
