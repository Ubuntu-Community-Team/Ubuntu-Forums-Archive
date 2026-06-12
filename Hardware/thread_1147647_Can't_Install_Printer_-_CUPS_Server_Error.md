---
title: "Can't Install Printer - CUPS Server Error"
date: 2009-05-03
forum: Hardware
---

### Post by ezertuchev on 2009-05-03
Hello,

I can't install my new Xerox Phaser 6130N Printer. The Printers dialog detects it ok, but when it tries to install it, I get a CUPS Server Error during the operation <<server-error-internal-error>>

Can anyone help me?

Thanks!

Eduardo

---

### Post by MSwal2846 on 2009-05-04
I have the same problem, but with a Xerox 5500DN printer!  I'm running:
 Ubuntu 9.04
 Kernel Linux 2..6.28.11-generic
 Gnome 2.26.1

Hardware
 Memory:   1.9GB
 Processor 0:  Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz
 Processor 1:  Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz

System Status
 Available disk space: 63.6 GiB

I was able to add the printer by going into CUPS via Firefox [http://localhost:631](http://localhost:631)

Thanks!

---

### Post by kwph on 2009-05-12
I was having the same problem with a Xerox Phaser 6300. Maybe the gutenprint drivers did not get installed properly with Jaunty? Anyway, I was able to install the printer by choosing the LPD printer install option, and then choosing the ps driver for the printer instead of the gutenprint driver option. (Choosing the gutenprint option gives the same error as the more automated method where you do not choose a PPD driver.)

---

### Post by halitech on 2009-05-19
for the phaser 6300 and the 5500, go here and download this driver, extract it and then add the printer

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_ZA&XCntry=ZAF&objid=61334&EULA=0&prodID=5500&Family=Phaser&ripId=&langs=English&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_ZA&XCntry=ZAF&objid=61334&EULA=0&prodID=5500&Family=Phaser&ripId=&langs=English&plats=Linux&Xtype=download&uType=)

the 6130 should be able to use the same download as it is just a collection of PPD files for all supported xerox printers.

---

