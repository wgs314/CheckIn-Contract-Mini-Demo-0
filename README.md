[README.md](https://github.com/user-attachments/files/29750127/README.md)
# CheckIn-Contract-Mini-Demo-0# CheckIn Contract — Mini Demo 0

一个基于 Solidity + Hardhat + ethers.js 的链上打卡 DApp，用于展示智能合约开发、前端交互和 MetaMask 集成。

An on-chain check-in DApp built with Solidity, Hardhat, and ethers.js — demonstrating smart contract development, frontend interaction, and MetaMask integration.

## 项目截图

![CheckIn Contract Screenshot](/outputs/CheckIn-Contract.png)

合约代码托管页面

## 技术栈

| 层级 | 技术 |
|------|------|
| 智能合约 | Solidity ^0.8.20 |
| 开发框架 | Hardhat v3 |
| 前端 | 原生 HTML + ethers.js v6 (UMD) |
| 钱包 | MetaMask (BrowserProvider) |
| 图片生成 | Edge Headless Screenshot |

## 项目结构

```
mini-demo-0/
├── contracts/
│   └── CheckIn.sol          # 打卡智能合约
├── frontend/
│   └── index.html           # 前端页面（MetaMask 交互）
├── scripts/
│   └── deploy.js            # 合约部署脚本
├── outputs/
│   └── CheckIn-Contract.png # 合约代码截图
├── hardhat.config.js        # Hardhat 配置
├── package.json
└── README.md
```

## 快速开始

### 1. 安装依赖

`npm install`

### 2. 本地编译合约

`npx hardhat compile`

### 3. 启动本地测试链

`npx hardhat node`

### 4. 部署合约

在新终端窗口：`node scripts/deploy.js`

部署后会输出合约地址，复制到 frontend/index.html 中的 CONTRACT_ADDR 常量。

### 5. 打开前端

直接在浏览器中打开 frontend/index.html，连接 MetaMask（切换网络到 Hardhat Local: 127.0.0.1:8545，Chain ID 31337），即可打卡交互。

## 合约接口

| 函数 | 描述 |
|------|------|
| checkIn() | 每日打卡，每人每天仅限一次 |
| getCheckInCount(address) | 查询指定地址累计打卡次数 |
| hasCheckedInToday(address) | 查询指定地址今天是否已打卡 |

### 事件

CheckInSuccess(address indexed user, uint256 timestamp, uint256 total) — 打卡成功时触发

## 作品集

从 Solidity 合约设计、Hardhat 本地开发链路到 MetaMask 钱包集成，实现了一条完整的链上 DApp 闭环，展示了合约编写 -> 本地测试链部署 -> 前端交互的全栈 Web3 开发能力。

## 后续推进方向

- 合约编译与本地测试链部署验证
- 编写 Hardhat 单元测试（Mocha + Chai）
- 前端增加多语言切换（中/英）
- 添加打卡排行榜（Leaderboard）视图
- 引入 OpenZeppelin 的 Ownable，增加管理员可选的额外激励功能（如连续打卡奖励）
- 部署到 Sepolia 测试网或 Linea 等 L2，前端切换网络支持多链
- 使用 Wagmi / Viem 替代 ethers.js UMD 以支持 React 项目结构
- 添加 NFT 徽章：连续打卡 N 天后铸造一枚 ERC-721 徽章
- 添加子图（The Graph）索引事件，支持更复杂的查询和统计
- GitHub CI 集成合约编译 + 测试流水线
