# B17 照片地圖 — GitHub 上傳說明

香港中文大學人類學系 1991 年東涌考察 B17 照片互動地圖。

## 開啟方式

直接開啟 `index_custom_v1.html` 即可（需透過本地伺服器，因為瀏覽器對 `file://` 的
XHR 有限制）。例如：

```bash
cd <此資料夾>
python3 -m http.server 8000
# 然後瀏覽 http://localhost:8000/index_custom_v1.html
```

## 檔案結構

```
index_custom_v1.html   主程式（三欄式互動地圖：篩選 / 地圖 / 照片詳情）
data/
  Clippedextent_1.png      預設顯示的總覽疊圖（799×691）
  5SED_7.jpg               東涌研究區分幅疊圖（4000×3220，JPEG）
  6SWC_6.jpg
  9SEA_2.jpg
  9SEB_8.jpg
  individualphotoB17_cleaned_9.js   42 筆照片紀錄的 GeoJSON
images/                    44 張照片 JPEG
css/  js/  legend/  webfonts/     Leaflet 與圖示資源
```

## 關於影像壓縮

原始 QGIS 匯出資料夾含有 4 張 500MB 以上的 PNG 掃描檔
（`dop9sea20210150_0.png`、`dop5sed20210158_3.png`、
`dop9seb20210150_4.png`、`dop6swc20210158_5.png`），
超過 GitHub 單檔 100MB 上限，無法直接上傳。

本資料夾已將對應的分幅圖縮圖並轉為 JPEG（quality 75，最長邊 4000px），
每張約 1.4–2.2MB，視覺上足以支撐地圖縮放。圖層控制中的「（高解析度）」項目
即對應這些壓縮後版本。

若日後取得原始高解析度檔案，可另行存放於 GitHub Releases 或 Git LFS。

## 功能

- 三欄版面：左欄篩選、中間地圖、右欄照片與 metadata
- 篩選：Place / Subject / Location precision（多選，AND 邏輯）
- Marker 聚合與選中高亮（縮放後自動還原選中狀態）
- 地圖上常駐 place_name 標籤
- 照片放大檢視（Lightbox，ESC 或點擊背景關閉）
- 「關閉」按鈕返回地圖與篩選清單
- 定點未知照片（B17P04、B17P44）置於左欄獨立區塊
- 響應式：桌面三欄 / 平板雙欄 / 手機分頁

## 資料來源

照片來源：香港中文大學人類學系
