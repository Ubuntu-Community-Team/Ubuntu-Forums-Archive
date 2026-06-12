---
title: "Printer Xerox Phaser 6000VB not working"
date: 2013-02-19
forum: Hardware
---

### Post by Viking84 on 2013-02-19
Hi all,

I've just bought a xerox phaser 6000VB color laser printer and can't get it to work on Xubuntu 12.10. I tried installing the official driver from Xerox, which is available at [http://www.support.xerox.com/support/phaser-6000/downloads/enus.html?operatingSystem=linux&fileLanguage=en_GB](http://www.support.xerox.com/support/phaser-6000/downloads/enus.html?operatingSystem=linux&fileLanguage=en_GB), but keep getting errors while trying to print (test page or doc, no matter what).

On the diagnose dialogue, I got a message saying saying "Server Not Exporting Printers" Enable the 'Publish shared printers connected to this system' which I did, but without chaning anything.

Now, I end up at the debugging screen, however the error log isn't really comprehensive to me. Can anybody help sort things out for me? I'm not exactly a pro on linux, so please take it easy on me ;-)

Here's the log:
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] POST / HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] No authentication data provided.
D [19/Feb/2013:21:18:16 +0100] [Client 18] 2.0 Get-Jobs 299
D [19/Feb/2013:21:18:16 +0100] Get-Jobs ipp://localhost/printers/
D [19/Feb/2013:21:18:16 +0100] [Job 19] Loading attributes...
D [19/Feb/2013:21:18:16 +0100] [Job 20] Loading attributes...
D [19/Feb/2013:21:18:16 +0100] [Job 21] Loading attributes...
D [19/Feb/2013:21:18:16 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] POST / HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] No authentication data provided.
D [19/Feb/2013:21:18:16 +0100] [Client 18] 2.0 Get-Jobs 300
D [19/Feb/2013:21:18:16 +0100] Get-Jobs ipp://localhost/printers/
D [19/Feb/2013:21:18:16 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] No authentication data provided.
D [19/Feb/2013:21:18:16 +0100] cupsdIsAuthorized: username=""
D [19/Feb/2013:21:18:16 +0100] [Client 18] WWW-Authenticate: Basic realm="CUPS", trc="y"
D [19/Feb/2013:21:18:16 +0100] [Client 18] Closing connection.
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] Accepted from localhost (Domain)
D [19/Feb/2013:21:18:16 +0100] [Client 18] GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] Authorized as chris using PeerCred
D [19/Feb/2013:21:18:16 +0100] cupsdIsAuthorized: username="chris"
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] Authorized as chris using PeerCred
D [19/Feb/2013:21:18:16 +0100] cupsdIsAuthorized: username="chris"
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] Authorized as chris using PeerCred
D [19/Feb/2013:21:18:16 +0100] cupsdIsAuthorized: username="chris"
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] PUT /admin/conf/cupsd.conf HTTP/1.1
D [19/Feb/2013:21:18:16 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:16 +0100] [Client 18] Authorized as chris using PeerCred
D [19/Feb/2013:21:18:16 +0100] cupsdIsAuthorized: username="chris"
I [19/Feb/2013:21:18:16 +0100] Installing config file "/etc/cups/cupsd.conf"...
D [19/Feb/2013:21:18:17 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [19/Feb/2013:21:18:17 +0100] [Client 18] Closing connection.
D [19/Feb/2013:21:18:17 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [19/Feb/2013:21:18:17 +0100] cupsdDeregisterPrinter(p=0x7fb29e780470(Xerox-Phaser-6000B), removeit=1)
I [19/Feb/2013:21:18:17 +0100] Generating printcap /var/run/cups/printcap...
D [19/Feb/2013:21:18:17 +0100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [19/Feb/2013:21:18:17 +0100] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [19/Feb/2013:21:18:17 +0100] Unknown directive JobPrivateAccess on line 89 of /etc/cups/cupsd.conf.
E [19/Feb/2013:21:18:17 +0100] Unknown directive JobPrivateValues on line 90 of /etc/cups/cupsd.conf.
E [19/Feb/2013:21:18:17 +0100] Unknown directive SubscriptionPrivateAccess on line 91 of /etc/cups/cupsd.conf.
E [19/Feb/2013:21:18:17 +0100] Unknown directive SubscriptionPrivateValues on line 92 of /etc/cups/cupsd.conf.
W [19/Feb/2013:21:18:17 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Xerox-Phaser-6000B-Gray..' already exists
W [19/Feb/2013:21:18:17 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Xerox-Phaser-6000B-CMYK..' already exists
W [19/Feb/2013:21:18:17 +0100] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Xerox-Phaser-6000B' already exists

Anyone knows what to do?

---

### Post by vinicius2 on 2013-11-28
Hi,

I solved the problem of my Xerox 6000B in Ubuntu 13.10 using the following method:
[http://www.chsd.com.br/index.jsp?c=Article&a=1010&id=23](http://www.chsd.com.br/index.jsp?c=Article&a=1010&id=23)

The article is in portuguese but basically you need to ddownload the RPM driver and uncompress it in the /usr folder.

After that you need to install some i386 libraries if you are using a x64 version of Ubuntu.
apt-get install -y libcups2:i386 libcupsfilters1:i386 libcupsimage2:i386

And then you restart cups and add the printer again.

It works perfectly now.

---

