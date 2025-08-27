專案簡介
- 目標：提供一個可快速啟動的最小型全端範本，涵蓋健康檢查 API、基礎前端頁面、OpenAPI 描述與（可選）資料庫結構。
- 特性：
  - 健康檢查端點（/health 或 /api/health）。
  - 最小 Next.js（pages）前端頁面與 API Route（若有建立）。
  - OpenAPI 3.0 規格檔（僅 MVP 端點）。
  - PostgreSQL 最小 schema（可選）。

快速開始（本地）
- 系統需求：
  - Node.js LTS（建議 >= 18）
  - pnpm 或 npm
  - （可選）PostgreSQL 14+（若使用資料庫）

- 步驟：
  1) 取得專案原始碼並進入目錄：
     - git clone <REPO_URL_PLACEHOLDER>
     - cd <PROJECT_DIR>
  2) 建立環境變數：
     - 複製 .env.example 為 .env（若有提供），補齊必要變數。
  3) 安裝依賴：
     - 使用 pnpm：pnpm install
     - 或使用 npm：npm install
  4) 啟動開發：
     - 單一應用於專案根目錄：
       - pnpm dev 或 npm run dev
     - 若採子資料夾（例如 web/）：
       - cd web && pnpm dev 或 npm run dev
  5) 檢查健康狀態（示例）：
     - 前端內建 API 路由（若有）：http://localhost:<PORT_PLACEHOLDER>/api/health
     - 獨立服務（若有）：http://localhost:<PORT_PLACEHOLDER>/health

部署概述
- 準備：
  - 設定必要環境變數（請參考 .env.example 的鍵名）。
  - 確認網路與埠號設定。
- 建置與啟動：
  - 前端：pnpm build && pnpm start（或 npm run build && npm run start）。
  - 後端：依您的部署目標（同機或分離）啟動服務。
- 資料庫（可選）：
  - 於目標環境建立資料庫並套用 schema（若有 db/database.sql）。
- 健康檢查與監控：
  - 部署完成後打 /health 或 /api/health 確認 { "status": "ok" }。

資料夾說明（若有建立）
- web/：Next.js 前端（pages/、pages/api/ 等）。
- api/：OpenAPI 3.0 規格檔（例如 api/openapi.yaml）。
- db/：PostgreSQL 最小 schema（例如 db/database.sql）。
- docs/：部署與架構補充文件（簡要）。
- .env.example：環境變數鍵名示意。

常用指令（擇一使用 pnpm 或 npm）
- 安裝依賴：pnpm install | npm install
- 開發模式：pnpm dev | npm run dev
- 建置產物：pnpm build | npm run build
- 啟動產物：pnpm start | npm run start

設定與環境變數
- 以最小原則配置，請在 .env 中填入必要鍵值（不要提交敏感資訊）。
- 未知或待定的鍵請以 PLACEHOLDER 註明，待實作時補齊。

注意事項
- 請勿在版本庫提交真實金鑰、密碼或真實網址。
- 未確定的端點、結構與連線資訊請保留 TODO 與 PLACEHOLDER。
- 本範本不依賴多餘第三方套件（除 Next.js 與 Node.js 內建能力）。

故障排除（簡要）
- 埠號被占用：調整環境變數中的 PORT 或更改啟動腳本。
- 環境變數缺失：比對 .env.example 的鍵名補齊。
- Schema 未套用：確認已於目標資料庫執行相對應 SQL。

下一步 TODO（精簡）
- 補齊 OpenAPI 規格並與實作對齊。
- 新增單元與端對端測試，涵蓋健康檢查與關鍵流程。
- 規劃 CI/CD（安裝依賴、建置、測試、部署）。
- 加入日誌與基本觀測性（請先定義等級與格式）。
- 若使用資料庫：設定最小 RLS/權限與遷移流程。
- 撰寫安全性與備援策略（速記清單）。