---
title: "Can't install Epson XP-410 with Ubuntu 14.04"
date: 2014-05-08
forum: Hardware
---

### Post by bryantarrington on 2014-05-08
I am trying to install drivers and have epson-inkjet-printer-201303w installing with Ubuntu 14.04 on Lenovo E2 Vision AMD but it only gets half way across (bar of progress) and never finishes.

Any help please???

thanks

---

### Post by pdc on 2014-05-11
Hi Bryan;

for the 410, I would go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and tap in 410 and I can either have [COLOR="#008000"]epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb[/COLOR] or [COLOR="#008000"]epson-inkjet-printer-201303w_1.0.0-1lsb3.2_i386.deb[/COLOR]  ........depending on whether one is 32 or 64bit: which system have you? (if you type arch in a terminal, it should tell you ..............)

is that what you did? 

(When clicking to download, I would select OPEN and open with gdebi installer if possible as that downloads and installs in one go ...............)

---

### Post by wainbee on 2014-06-03
Thank you pdc, your advice was spot on!

Like Bryan, I too attempted to install the Epson XP-410 using the Add Printer facility on Xubuntu 14.04 (AMD64) but the progress bar advances half-way and never finishes.  Perhaps the Ubuntu installer for the Epson XP-410 is unable to install all the dependencies.  I downloaded the (epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb) driver and tried to install using the Ubuntu Software Center... same thing, the install never finished, no error messages.  Next, I installed gdebi based on the last line of your advice.  I opened the downloaded driver file and installed using gdebi...  I believe gdebi mentioned installing 30 dependencies but the install went quickly and completed.  This is a fabulous and inexpensive Wi-Fi printer/scanner and Epson is good enough to supply Linux drivers.  It's working great, thanks again pdc.  The secret lies in using gdebi installer which now ranks tops in my book!

---

### Post by pdc on 2014-06-03
thanks wainbee; that's great;

fascinating to hear your experience; I would have thought ubuntu software centre would have gdebi at its core; 

the 410 also does scanning.............have you installed iscan that epson supply?

If you do that, Epson say install the DATA package first.......... post back if you want some pointers; pleased to help;

---

### Post by wainbee on 2014-07-02
Epson XP-410 Printer/Scanner installation  64bit Ubuntu/Xubuntu


Use Gdebi and install drivers in the order listed below:


Printer
1.   epson-inkjet-printer-escpr_1.4.0-1lsb3.2_amd64.deb


2.   epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb


Scanner
3.   iscan-data_1.28.0-2_all.deb


4.   COREiscan_2.29.3-1~usb0.1.ltdl7_amd64.deb


5.   iscan-network-nt_1.1.1-1_amd64.deb




Re: 32bit Ubuntu/Xubuntu


as of June 2014, am finding this driver file corrupt:  epson-inkjet-printer-201303w_1.0.0-1lsb3.2_i386.deb
no success yet installing Epson XP-410 on 32 bit systems

---

### Post by pdc on 2014-07-02
thanks

when you say

> Use Gdebi and **install drivers in the order listed below**:


Printer
1. epson-inkjet-printer-escpr_1.4.0-1lsb3.2_amd64.deb


2. epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb

I had understood the ESC/P-R Driver was a generic driver; so I saw it as an "either-or" situation: mostly, folks would likely want the full feature driver

[http://download.ebz.epson.net/man/linux/escpr.html](http://download.ebz.epson.net/man/linux/escpr.html)

Epson say > This software is a filter program used with the Common UNIX Printing System (CUPS) on the Linux platform. The software offers high quality printing with Epson color ink jet printers. 

for the other driver, [http://download.ebz.epson.net/man/linux/escp.html](http://download.ebz.epson.net/man/linux/escp.html) Epson say > Epson Inkjet Printer Driver is a printer driver software to print with high quality from Linux by using a Epson made inkjet printer. 

......have you seen advice to install the generic (escpr)first, and then the 201303w ?

---

### Post by wainbee on 2014-07-09
Thanks for checking this PDC.  I believe you are correct that the 'escpr' driver need not be installed in step #1 above.


The Epson documentation is a little confusing, I may have mistook the instruction below to imply that **all** drivers need to be installed in a particular order:
*"In order to install Epson Inkjet Printer Driver, you need to install the package of LSB 3.2 beforehand."*


Please let us know if you have any experience installing the XP-410 drivers on 32 bit systems.  I believe the 32bit Debian driver was converted from an RPM version but seems to be lacking several dependencies.


Also wondering if anyone has tried the Epson PC-Fax Driver.




Below is the amended Epson XP-410 64bit driver installation order:


[SIZE=3]**Epson XP-410 Printer/Scanner installation 64bit Ubuntu/Xubuntu**[/SIZE]


Use Gdebi and install drivers in the order listed below:

Download from:  [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)


**Printer:**
1. epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb


**Scanner:**
2. iscan-data_1.28.0-2_all.deb
3. COREiscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
4. iscan-network-nt_1.1.1-1_amd64.deb

---

### Post by pdc on 2014-07-09
> if you have any experience installing the XP-410 drivers on 32 bit systems.

we put the Epson 410 driver onto a 12.04 32bit ubuntu and it is fine

---

