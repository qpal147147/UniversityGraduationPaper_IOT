# 大學畢業專題
作品名稱為：***遠端智慧型運送列車***<br>
為IOT物聯網的作品，由4人團隊所創作。<hr>

## 使用語言<br>
* **前端**：HTML、CSS、JavaScript、JQuery
* **後端**：PHP
* **DataBase**：MySQL

## 使用套件<br>
1. [Milligram](https://milligram.io/)：CSS樣式
2. [Semantic UI](https://semantic-ui.com/)：CSS樣式
3. [Echarts](https://echarts.apache.org/zh/index.html)：視覺化圖表呈現

## 作品摘要<br>
本作品透過 WEB 網頁端進行各項控制，並將資訊傳至運送車上的微電腦來進行運送流程。網頁端主要分成客戶訂料介面、管理員控管介面及資料庫查詢介面，使用者透過訂料介面選取送達位置及所需物料並預覽檢查訂單，完成後將訂單資訊送達至管控介面。管理員在接收到訂單後，可隨時依狀況進行訂單上的修正(刪除、更改)，並將資訊透過 WIFI 傳達至列車上的微電腦進行判斷與控制。<br><br>
微電腦接收資訊後，配合運送車上的光感測器偵測當前位置並傳送訊號至微電腦統一處理及判斷，決定運送車的行駛路徑與停止站點。當到達指定站點時蜂鳴器會發出聲響提醒使用者拿取物料。而列車所在位置也會透過 WIFI 傳回至伺服器並在網頁上顯示目前的位置，以供管理員及使用者方便查看及維護。<br><br>
當列車運送完畢後系統會將訂單備份至資料庫，提供未來查詢及數據分析使用，以利控管物料減少資源的浪費。<br><br>

## 作品架構<br>
網站透過WIFI傳達資訊給WIFI模組ESP8266，透過8052單晶片讀取解析並驅動列車行駛，最後回傳即時點位訊息至網站。<br>
> **使用者**
>>使用者定料介面<br>
>>確認訂單介面<br>
>>使用者查詢訂單介面<br>
>>列車當前位置介面<br>

> **管理員**
>>管理員登入介面<br>
>>管理員管控介面(修改、刪除、確認運送)<br>

> **歷史資料查詢**
>>登入介面<br>
>>歷史資料查詢介面(日期區間查詢、年月份查詢)<br>

## 文件描述<br>
|         文件        |                       描述                      |
|         ---         |                       ---                      |
|**index.html**       |  使用者定料介面                                 |
|**stock.php**        |  顯示物料剩餘數量                               |
|**confirm.php**      | 再次確認使用者所選物料之介面                     |
|**Session.php**      | 將所選物料存入資料庫裡                           |
|**viewOrder.php**    | 使用者可檢視所有訂單之介面                       |
|**trainPath.html**   |  使用者可檢視列車目前所在位置之介面               |
|**loginManager.php** |  管理員管控網站之登入介面                        |
|**Manager.php**      | 管理員管控介面，負責處理所有訂單並隨時根據狀況修改 |
|**position.php**     |  負責讀取txt檔案內資料並顯示                     |
|**position.txt**     |  接收ESP8266所傳回的資訊                        |
|**loginHistory.php** |  歷史資料查詢網站之登入介面                      |
| **history.php**     | 顯示所有過往「已處理」之訂單                     |
|**8052.a51**         |  為8052單晶片進行所有處理與發送訊號的程式碼       |
|**style**            |  存放所有素材，CSS、JS、IMG                     |

## 文件關係圖<br>
![Organization Chart](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/OrganizationChart.jpg)

## 整體流程<br>
1. 使用者透過網頁進行定料。
2. 管理員透過管控介面查看訂單。
3. 將訂單狀態變更為處理中，並啟動列車至訂單指定位置。
4. 透過WIFI模組ESP8266接收網頁資訊，並傳送至8052單晶片處理。
5. 列車每經過一個點位光感測器會偵測並回傳至8052，並推斷出當前位置，且同步顯示於網頁上。若當前位置符合訂單位置則停止行駛，並啟動蜂鳴器。
6. 當列車回至起始位置後，管理員將狀態更改為已處理並刪除。
7. 已處理完畢訂單會備份至資料庫，透過查詢介面可查看。並可選擇任意時間區間或年月份進行整體查詢。
![Organization Chart](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/flowchart.jpg)

## 軟體作品圖<br>
* 使用者介面
![User interface](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/index.jpg)
* 再次確認訂單
![Confirm form](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/confirm.jpg)
* 查看當前列車位置
![Train path now](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/TrainPath.jpg)
* 查看目前所有訂單
![View order](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/viewOrder.jpg)
* 管理員登入介面
![Login manager interface](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/loginManager.jpg)
* 管理員介面
![Manager interface](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/manager.jpg)
* 歷史資料查詢登入介面
![Login history interface](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/loginHistory.jpg)
* 歷史資料查詢系統
![history system](https://raw.githubusercontent.com/qpal147147/UniversityGraduationPaper_IOT/master/sampleImage/history.jpg)
