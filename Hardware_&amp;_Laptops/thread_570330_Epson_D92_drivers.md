---
title: "Epson D92 drivers"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by pocketsized on 2007-10-08
hi all

the avasys site for Epson D92 drivers is down:

[http://avasys.jp/hp/page000001100/hpg000001022.htm](http://avasys.jp/hp/page000001100/hpg000001022.htm)

can anyone point me to a mirror or does someone have a copy of the drivers they can send me?

thanks
dave

---

### Post by kat_ams on 2008-05-22
The drivers are available again from the Epson Avasys site again after I sent an e-mail to Epson Avasys. This time the drivers are in a Tarball. I could not get them to install yet properly. If anyone else can get them to work would be greatly appreciated to find out how.

[http://www.avasys.jp/lx-bin2/linux_e/ink/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/ink/DL2.do")

---

### Post by kat_ams on 2008-05-22
> **kat_ams said:**
> The drivers are available again from the Epson Avasys site again after I sent an e-mail to Epson Avasys. This time the drivers are in a Tarball. I could not get them to install yet properly. If anyone else can get them to work would be greatly appreciated to find out how.

[http://www.avasys.jp/lx-bin2/linux_e/ink/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/ink/DL2.do")

kat@leon:~/Desktop$ sudo ./pips-sc90-Redhat9-3.0-CLGE.install 
[sudo] password for kat: 
Verifying archive integrity... All good.
Uncompressing pips.............

##########################################################################

                  Photo Image Print System for Linux

           Copyright (C) SEIKO EPSON CORPORATION 2005-2006.

##########################################################################

This will install the printer driver for Stylus C90.


*** Documents currently printing will be canceled ***

If a document is currently printing, please wait until printing finishes
before installing the driver.

Installation will start.
Do you want to continue? (Yes/No): Yes
Installing...

Already installed pips-core. (3.0)
Already installed pips-extension. (3.0)
Already installed pips-gtk2. (3.0)
Already installed pips-cups. (3.0)
Already installed pips-lpr. (3.0)
Already installed pips-Redhat9. (3.0)
Already installed pips-sc90. (3.0)
Add printer setting at spool system...
Startup ekpd-tool...
sh: /sbin/pidof: not found
PIPS Warning: Printer not install.
Installation is complete.
Please refer to the document below for information on how to use the printer
driver.

(English)  /usr/share/doc/pips-core-3.0/UsersManual.txt
(Japanese) /usr/share/doc/pips-core-3.0/UsersManual_ja.txt

Also please refer to the document below for information specific to the
printer.

/usr/share/doc/pips-sc90-3.0/Stylus_C90_Manual.txt

*** Quit ***
<Enter>read: 250: arg count
kat@leon:~/Desktop$

---

