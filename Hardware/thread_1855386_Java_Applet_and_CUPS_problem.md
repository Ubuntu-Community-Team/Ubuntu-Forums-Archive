---
title: "Java Applet and CUPS problem"
date: 2011-10-06
forum: Hardware
---

### Post by cipher_neo on 2011-10-06
Hi guys, 

I have developed a ruby on rails pos system that needs to access a receipt printer from the browser. I can do so by using a java applet and using the java print APIs.

It works fine on windows, but the cups config is giving me some trouble.

I am trying to print from the java applet to a printer that I have set up with cups on Ubuntu 11.04

I am on chrome and using the java6 plugin (sun-java6-plugin in package manager).

When I try to print, I see that java tries to access a printer via the cups interface "localhost:631". It tries to connect to the printer I have set up and it eventually fails with a "connection refused" error, followed by a "printer service not found".

I have tried the exact same configuration from another machine running ubuntu and the exact same problem occurs, so I must be doing something wrong.

Any ideas?



Here is the stack trace from the java console:

network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
security: Automation: Accept printing
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
network: Connecting [http://localhost/crossdomain.xml](http://localhost/crossdomain.xml) with proxy=DIRECT
network: Connecting [http://localhost:80/](http://localhost:80/) with proxy=DIRECT
java.security.PrivilegedActionException: java.net.ConnectException: Connection refused
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.deploy.net.CrossDomainXML.check(CrossDomainXML.java:355)
	at com.sun.deploy.net.CrossDomainXML.check(CrossDomainXML.java:149)
	at sun.plugin2.applet.Applet2SecurityManager.checkConnect(Applet2SecurityManager.java:508)
	at sun.net.[www.protocol.http.HttpURLConnection.checkURLFile(HttpURLConnection.java:622](www.protocol.http.HttpURLConnection.checkURLFile(HttpURLConnection.java:622))
	at sun.net.[www.protocol.http.HttpURLConnection.writeRequests(HttpURLConnection.java:459](www.protocol.http.HttpURLConnection.writeRequests(HttpURLConnection.java:459))
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1193](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1193))
	at sun.print.CUPSPrinter.getDefaultPrinter(CUPSPrinter.java:251)
	at sun.print.UnixPrintServiceLookup.getDefaultPrintService(UnixPrintServiceLookup.java:506)
	at javax.print.PrintServiceLookup.lookupDefaultPrintService(PrintServiceLookup.java:166)
	at sun.print.RasterPrinterJob.getPrintService(RasterPrinterJob.java:430)
	at sun.print.RasterPrinterJob.defaultPage(RasterPrinterJob.java:1517)
	at sun.print.RasterPrinterJob.setPrintable(RasterPrinterJob.java:953)
	at receiptprinter.ReceiptPrinter.printReceipt(ReceiptPrinter.java:30)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at sun.plugin.javascript.JSInvoke.invoke(JSInvoke.java:20)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at sun.plugin.javascript.JSClassLoader.invoke(JSClassLoader.java:72)
	at sun.plugin2.liveconnect.JavaClass$MethodInfo.invoke(JavaClass.java:123)
	at sun.plugin2.liveconnect.JavaClass$MemberBundle.invoke(JavaClass.java:278)
	at sun.plugin2.liveconnect.JavaClass.invoke0(JavaClass.java:429)
	at sun.plugin2.liveconnect.JavaClass.invoke(JavaClass.java:410)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo$DefaultInvocationDelegate.invoke(LiveConnectSupport.java:980)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo$3.run(LiveConnectSupport.java:637)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo.doObjectOp(LiveConnectSupport.java:632)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo$LiveConnectWorker.run(LiveConnectSupport.java:1743)
	at java.lang.Thread.run(Thread.java:662)
Caused by: java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:351)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:213)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:200)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
	at java.net.Socket.connect(Socket.java:529)
	at sun.net.NetworkClient.doConnect(NetworkClient.java:161)
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:394](www.http.HttpClient.openServer(HttpClient.java:394))
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:529](www.http.HttpClient.openServer(HttpClient.java:529))
	at sun.net.www.http.HttpClient.<init>(HttpClient.java:233)
	at sun.net.[www.http.HttpClient.New(HttpClient.java:306](www.http.HttpClient.New(HttpClient.java:306))
	at sun.net.[www.http.HttpClient.New(HttpClient.java:323](www.http.HttpClient.New(HttpClient.java:323))
	at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:970](www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:970))
	at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:911](www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:911))
	at sun.net.[www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:836](www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:836))
	at com.sun.deploy.net.CrossDomainXML$2.run(CrossDomainXML.java:359)
	... 34 more
security: Automation: Accept printing
security: Automation: Accept printing
network: Connecting [http://localhost:631/EPSONTMT20](http://localhost:631/EPSONTMT20) with proxy=DIRECT
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
security: Automation: Accept printing
security: Automation: Accept printing
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
security: Automation: Accept printing
security: Automation: Accept printing
network: Connecting [http://localhost:631/EPSONTMT20](http://localhost:631/EPSONTMT20) with proxy=DIRECT
network: Connecting [http://localhost:631/](http://localhost:631/) with proxy=DIRECT
security: Automation: Accept printing
java.awt.print.PrinterException: No print service found.
	at sun.print.RasterPrinterJob.print(RasterPrinterJob.java:1275)
	at sun.print.RasterPrinterJob.print(RasterPrinterJob.java:1247)
	at receiptprinter.ReceiptPrinter.printReceipt(ReceiptPrinter.java:33)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at sun.plugin.javascript.JSInvoke.invoke(JSInvoke.java:20)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at sun.plugin.javascript.JSClassLoader.invoke(JSClassLoader.java:72)
	at sun.plugin2.liveconnect.JavaClass$MethodInfo.invoke(JavaClass.java:123)
	at sun.plugin2.liveconnect.JavaClass$MemberBundle.invoke(JavaClass.java:278)
	at sun.plugin2.liveconnect.JavaClass.invoke0(JavaClass.java:429)
	at sun.plugin2.liveconnect.JavaClass.invoke(JavaClass.java:410)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo$DefaultInvocationDelegate.invoke(LiveConnectSupport.java:980)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo$3.run(LiveConnectSupport.java:637)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo.doObjectOp(LiveConnectSupport.java:632)
	at sun.plugin2.main.client.LiveConnectSupport$PerAppletInfo$LiveConnectWorker.run(LiveConnectSupport.java:1743)
	at java.lang.Thread.run(Thread.java:662)

---

### Post by cipher_neo on 2011-10-13
Still having this problem, has anyone got any ideas? please

---

### Post by cipher_neo on 2011-10-21
anybody?

---

