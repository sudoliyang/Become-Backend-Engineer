# 通訊
還記得我們上一篇 [初探 Web 的世界](https://ithelp.ithome.com.tw/articles/10192699), 提到的通訊協定，在網路的世界也是一樣，我們連結到對方電腦就跟打電話一樣，我們必須有對方的 IP Address 才能夠跟對方伺服器連線，同時電腦跟電腦之間也會有自己的通訊格式來交換資料，我們稱之為通訊協定(Protocal)，常見的通訊協定有 TCP、HTTP、SSH、UDP 等等，這些不同的通訊協定好讓我們在面對不同的使用情境，能夠選擇最適合的通訊方式。

以上篇的故事為例，我們透過電話傳遞訊息給櫃檯的服務生請他協助我訂位，他將訊息傳遞給小D同事，小D同事在後端處理好訂位的細節並協助我們完成訂位。在網際網路我們每天所使用的 HTTP 通訊協定，定義了不同的 Method，讓我們能夠在不同的需要使用不同的 HTTP Method, 了解更多 [HTTP Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

今天我們要跟IT幫餐廳訂 12/25 晚上的火雞餐，我們進到IT幫餐廳的訂票的頁面，就如同我們打電話給櫃檯的服務生告訴他們我們要訂位一樣，我們會先取得目前訂位的狀態，在 HTTP 請求我們會使用 GET 的 Method, 來拿取得某個特定的資源，就如同我們在電話裡：「喂，IT幫餐廳嗎？ 請問12/25 晚上還有空位嗎」

假設 IT幫餐廳的訂票網址是 http://restaurant.ithome.com.tw/orderStatus，當我們用瀏覽器瀏覽此頁面時，瀏覽器會自動幫我們發出像是這樣的請求在拿到伺服器回覆的訊息之後瀏覽器載入 HTML、CSS 將網頁渲染出來。

> HTML 用來描述網頁的結構，例如說他應該有幾個標題、子標題、段落。
> CSS 用來撰寫各個區塊的樣式，像是標題應該幾個 px、設定成什麼顏色

```
> GET /orderStatus HTTP/1.1
> Host: restaurant.ithome.com.tw
> Accept: */*
>
< HTTP/1.1 200 OK
< Connection: keep-alive
< Content-Type: text/html
< Content-Length: 1000
...
```

當網頁呈現出來 12/25 有空位，我們填寫完訂位的資訊後按下送出的按鈕，在 HTTP 有著一個 Method 是 POST，就像把內容放在信封一樣，把我們的訂票資訊封起來傳送到特定的網址。
此時瀏覽器對 Server 發出了一個 POST 的請求
```
> POST /anything HTTP/1.1
> Host: restaurat.ithome.com.tw
> Accept: */*
> Content-Length: 26
> Content-Type: application/x-www-form-urlencoded
> name=sudoliyang&date=12/25

< HTTP/1.1 200 OK
< Connection: keep-alive
< Content-Type: text/html
< Content-Length: 1000
...
```
可以看見我們將姓名與訂位的日期夾帶在裡頭，就像我們告訴接聽電話的人員我們訂位資訊一樣，接著伺服器回覆給我們訂位完成的 HTML 跟 CSS，讓我們看到訂位完成的結果。

經過這個章節希望大家都對網際網路的通訊有更多的認識與了解，了解到平時每天使用瀏覽器逛網站得到不同的資訊時原來有這麼多的知識在裡頭！
