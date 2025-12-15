打掃工作分配系統 (Cleaning Task Assignment System)

這是一個基於 Firebase Firestore 實時資料庫和 GitHub Pages 部署的單頁應用程式（SPA），旨在協助團隊進行打掃工作分配前的測驗與結果發布。

整個系統由三個獨立的 HTML 文件組成，但它們共用相同的 Firebase 後端配置。

檔案結構

整個應用程式運行在三個主要的 HTML 文件中：

index.html (系統導航頁 - 主入口)

participant.html (參與者測驗與結果頁)

host_view.html (主持人儀表板與分組發布頁)

🚀 快速上手與使用指南

1. index.html (導航頁)

這是網站的起始頁面，當您訪問 GitHub Pages 的主網址時，會自動載入此頁面。它提供了快速進入「參與者入口」或「主持人儀表板」的連結。

2. participant.html (參與者入口)

此頁面供所有參與者使用。

功能：

輸入姓名並勾選同意後，開始計時測驗 (30 分鐘)。

測驗結果將根據答案傾向分為 S (掃拖)、Z (整理)、H (活動) 三類並提交到資料庫。

測驗提交後，頁面會顯示個人的傾向分數，並實時監聽主持人發布的最終分組結果。

數據操作：

每位參與者的提交紀錄會使用他們的姓名作為文件 ID 儲存在 Firestore 的 /artifacts/{appId}/public/data/submissions 集合中。

3. host_view.html (主持人儀表板)

此頁面專供主持人或管理員使用，以查看測驗數據和發布最終分組。

功能：

實時查看所有參與者的姓名、傾向分析（S/Z/H 分數）和提交時間。

透過文字輸入框定義最終分組（例如：籤一：公區前 (掃拖組) 的組員名單）。

點擊「發布最終分組結果」按鈕，將分組結果推送到 Firestore。

提供「清空所有提交紀錄」功能，用於測試或重置整個系統。

數據操作：

所有提交數據從 /artifacts/{appId}/public/data/submissions 實時讀取。

最終分組結果儲存在 /artifacts/{appId}/public/data/FINAL_ASSIGNMENT_STATUS/team_list 文件中。

⚙️ 系統技術棧

前端框架：原生 HTML, JavaScript (ES modules)

CSS 框架：Tailwind CSS (CDN)

資料庫：Google Firebase Firestore

認證：Firebase Anonymous Auth / Custom Token Auth

部署環境：GitHub Pages / Canvas

⚠️ 重要：GitHub Pages 檔案結構

請確保您的專案檔案結構如下，以確保網址可以正確訪問：

/ (根目錄)
|-- README.md  <-- 您剛新增的說明文件
|-- index.html     <-- 網站入口導航頁
|-- participant.html  <-- 參與者頁面
|-- host_view.html   <-- 主持人頁面
