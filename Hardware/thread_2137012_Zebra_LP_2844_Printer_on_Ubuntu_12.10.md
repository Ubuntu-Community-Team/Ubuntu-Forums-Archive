---
title: "Zebra LP 2844 Printer on Ubuntu 12.10"
date: 2013-04-19
forum: Hardware
---

### Post by matt238 on 2013-04-19
Hi,

I'm using ubuntu 12.10 and I'm trying to install a Zebra printer (Zebra LP 2844). I almost successfully installed it (it prints documents), however, when I try to print thing with Zebra code EPL2, the printer prints only the text and don't interpret it. I tried to use other drivers but when I change it, the printer do not print anymore. Do you have any idea to fix it? Thanks.

PS : I'm using this ppd : [http://andis63.homeftp.net/downloads/packages/cups/cups-1.5.0/ppdc/ppd/zebraep2.ppd](http://andis63.homeftp.net/downloads/packages/cups/cups-1.5.0/ppdc/ppd/zebraep2.ppd)

---

### Post by oldfred on 2013-04-19
Years ago with Windows I had similar issues with setting up our Zebra printers in our Korean plant. Their version of Windows did not have the plain ASCII print driver as they never needed it to print in Korean.  You need a print driver that passes everything thru.

This is now old and I have not checked it still valid.
Zebra & raw print device:
[http://code.google.com/p/jzebra/](http://code.google.com/p/jzebra/)
[http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu](http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu)

Edit also found this:
[http://opennomad.com/content/raw-cups-configuration-challenge](http://opennomad.com/content/raw-cups-configuration-challenge)

---

### Post by matt238 on 2013-04-22
Thank you so much ! The 2nd link worked perfect for me !

---

