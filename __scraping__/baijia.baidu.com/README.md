
StackOverflow: [https://stackoverflow.com/a/47634703/1832058](https://stackoverflow.com/a/47634703/1832058)

---

It seems this sever sends file with string `favicon.ico` if you have incorrect `USER-AGENT`

Try with extra option which looks like correct `USER-AGENT` and you get HTML file.

    scrapy shell -s USER_AGENT="Mozilla/5.0" https://baijia.baidu.com

And then `response.xpath` will work.

    In [1]: response.xpath('/html/head/title/text()').extract_first()
    Out[1]: '首页-百家号'

You can get better `USER-AGENT` from your browser using page [httpbin.org](https://httpbin.org)
