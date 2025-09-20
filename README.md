# app-configuration

集中管理项目所需的配置、密钥、账号信息等，避免分散存放带来的混乱。
适用于多种场景：

* **后端项目**：如 Python、Spring Boot、Node.js 等的配置文件（数据库密码、API Key 等）。
* **办公账号**：Office、邮件、会议工具等账号密码。
* **个人账号**：QQ、游戏账号、论坛账号等。

---

## 📂 项目结构

```
app-configuration/
├── README.md                # 项目说明
├── configs/                 # 各类项目配置
│   ├── python/              # Python 项目相关配置
│   ├── spring/              # Spring Boot 项目配置
│   ├── node/                # Node.js 项目配置
│   └── others/              # 其他项目
├── accounts/                # 账号信息存放
│   ├── office/              # 办公账号
│   ├── social/              # 社交账号（QQ、微信等）
│   └── games/               # 游戏账号
└── secrets/                 # 敏感密钥（建议加密存放）
```

---

## 🔐 使用建议

1. **本地存储**

   * 不要直接上传真实敏感信息到公开仓库。
   * 如果必须放到 Git 仓库，请设置为 **私有库**。

2. **加密保护**

   * 推荐使用 [git-crypt](https://github.com/AGWA/git-crypt) 或 [sops](https://github.com/mozilla/sops) 对敏感文件加密。
   * 或者简单地用压缩包 + 密码的方式管理 `secrets/` 目录。

3. **配置分离**

   * 开发环境、测试环境、生产环境的配置要分开存放，例如：

     ```
     configs/spring/dev/
     configs/spring/test/
     configs/spring/prod/
     ```

4. **最小可见原则**

   * 哪个账号/密码只给需要的人，避免所有人都能看到。

---

## 🚀 使用方式

* Python 项目示例（使用 `.env` 文件）：

  ```bash
  DATABASE_URL=postgresql://user:password@localhost:5432/db
  API_KEY=your_api_key_here
  ```

* Spring Boot 项目示例（`application.yml`）：

  ```yaml
  spring:
    datasource:
      url: jdbc:postgresql://localhost:5432/db
      username: user
      password: password
  ```

* 账号存放示例（`accounts/social/qq.md`）：

  ```markdown
  # QQ 账号
  - 用户名: example@qq.com
  - 密码: ********
  - 绑定手机号: 138****8888
  ```

---

## ⚠️ 安全警告

* 切勿将此仓库设为公开，否则所有敏感信息可能泄露。
* 建议定期更换密码/API Key。
* 建议启用双重认证（2FA）提升账号安全。

---

## 📌 维护说明

* 新增配置或账号时，请按目录分类存放。
* 建议在提交前执行以下命令，避免误传敏感信息：

  ```bash
  git status
  git diff
  ```
* 如果不小心提交了敏感信息，请第一时间在平台上重置密码/API Key。

---
