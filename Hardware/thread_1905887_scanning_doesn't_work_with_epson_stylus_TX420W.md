---
title: "scanning doesn't work with epson stylus TX420W"
date: 2012-01-07
forum: Hardware
---

### Post by andres.ordonez on 2012-01-07
Hi, scanning doesn't work (usb or wireless) with 'all in one' EPSON Stylus TX420W. I'm using ubuntu 10.04 and have already installed the driver (epson-inkjet-printer-nx420_1.0.0-1lsb3.2_amd64.deb) from AVASYS at

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

I'm running ubuntu 10.04. 

Printing works fine. Xsane detects the scaner but when pressing the Scan button it says 'Error during read: Error during device I/O.' and not only it doesn't scan but it also leaves the printer/scaner useless (the LEDs in the printer/scaner blink, it can't be used by other computers and it doesn't respond to other buttons besides On/Off)

The scaner works fine when using with ubuntu 11.10 (at another computer). The driver installed in this computer is the one suggested by ubuntu when detecting the printer/scaner, I think this driver is different from the one downloaded from AVASYS but I'm not sure (how can I check the driver installed?)

Thanks in advance

---

### Post by andres.ordonez on 2012-01-08
Well I've partially solved the problem with scanning. I uninstalled the epson related packages, and then downloaded and installed the modules:

ESC/P-R Driver
core package&data package
network plugin package

from [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Every time I start xsane I select the epkowa backend.

I can scan only when connected via USB. Wireless scanning does not work.

---

