## WebAPIとは？  

まずAPIとは、「Application Programming Interface」の略です。  
どんなアプリケーションでも共通で使える機能のことで、  
自分で１からプログラムを作成しなくても、APIを使うことで手間が省けます。  
WebAPIはインターネットを経由してプログラムを呼び出し、  
その結果を受け取ることができます。  
  
**つまり、インターネットに公開されているWebAPIを使えば、**  
**より効率的にアプリケーションを開発することができるようになります。**  

![WebAPIとは](https://raw.githubusercontent.com/tamken999/APIとは.jpg)  
  
  
## どのように動作するのか？  
  
仕組みはWebブラウザと似ています。Webブラウザは、  
あるサイトが見たいと思ったら、サイトのurlを指定し、  
そのサーバに「見たいからデータを送ってくれ」と要求を出します。  
要求を出すときはHTTPを利用します。  
そしてHTMLが送られてきてサイトが表示されます。  

![Webブラウザ](https://raw.githubusercontent.com/tamken999/webブラウザ.jpg)  

WebAPIも同じようにHTTPで要求を出し、そして  
プログラムが必要とするデータが、主にJSONで送られてきます。  
  
![WebAPI](https://raw.githubusercontent.com/tamken999/WebAPI.jpg)  
  
  
## WebAPIの例  

実際に例を見てみましょう。  
今回は、郵便番号のWebAPIを利用します。  
必要となるurlはこちら  
  
http://zipcloud.ibsnet.co.jp/api/search?zipcode=#######  
  
このurlの最後に郵便番号７桁を入れることで、  
その結果がJSONで返ってきます。  

    {
    	"message": null,
    	"results": [
    		{
    			"address1": "東京都",
    			"address2": "立川市",
    			"address3": "高松町",
    			"kana1": "ﾄｳｷｮｳﾄ",
    			"kana2": "ﾀﾁｶﾜｼ",
    			"kana3": "ﾀｶﾏﾂﾁｮｳ",
    			"prefcode": "13",
    			"zipcode": "1900011"
    		}
    	],
    	"status": 200
    }  
    
"results"には郵便番号に応じたデータが表示されています。  
"massage"にはなにかしらエラーが起きた場合にその原因が表示されます。  
"status"ではエラーの種類を番号で示しています。  
  400番代なら入力に誤りがあります。  
  500番代ならAPI内部でエラーが起きています。等々。  
  
  
## WebAPIの活用  
  
JSONで値が返ってきても、それだけでは味気ないので、  
Rubyの標準ライブラリ、json.rbで文字列を加工することも可能です。  
工夫してみましょう。