# CAL 流程设计

## 素材上链的考虑

### Pros
1. 素材内容不可更改，可以更好地进行确权（虽然仅仅是确权）
1. 可以增加Token的适用范围

### Cons
1. 产生额外的 gas 费用
1. 操作流程的复杂化（包括钱包与账号绑定的流程）

### 考虑方面1
#### 事实
1. 从区块链的设计理念方面考虑，“上链”的动作应该是由用户操作。
1. 从安全角度考虑，将 IFPS Hash 写入 ERC721 Token 的动作不能交给客户端完成；写入 Hash 的动作只能二选一：服务器或者智能合约。实现上从服务器写入更为现实。

#### 建议
流程应该这样设计：
1. 用户上传资源
1. 用户选择手动创建 ERC721 Token
1. 创建 Token 成功之后，客户端将创建好的 Token 信息发送到服务器
1. 服务器将 IPFS hash 写入之前创建的 Token

### 考虑方面1
#### 事实
对于大多数人来讲，确权并不是一个硬需求。但是如果在一开始就要求拥有钱包以及了解如何操作，可能会使得使用成本变得非常高。

#### 建议
创建 ERC721 Token 这一步可以选择忽略。采用传统的支付方式进行交易。