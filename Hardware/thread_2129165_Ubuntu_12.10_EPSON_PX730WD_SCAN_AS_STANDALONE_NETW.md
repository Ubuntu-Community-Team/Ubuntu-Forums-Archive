---
title: "Ubuntu 12.10 EPSON PX730WD SCAN AS STANDALONE NETWORK DEVICE"
date: 2013-03-25
forum: Hardware
---

### Post by sgk on 2013-03-25
To scan on Epson Stylus Photo PX730WD when is connected to your home LAN as a standalone device (not connected to a PC but directly to the LAN)
Goto EPSON DOWNLOAD site and download
1) Printer driver (epson-inkjet-printer-201112w_1.0.0-1lsb3.2_amd64.deb or the i386 one)
2) Scanner driver (iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb or the i386 one)
3) Scanner data (iscan-data_1.22.0-1_all.deb)

in the download site search for OS=linux, product=artisan and locate artisan  and from the table locate network plugin package and download it
4) network plugin package (iscan-network-nt_1.1.0-2_amd64.deb or the i386 one)

Then install 1) Printer driver, 2) scanner data, 3) scanner driver
then goto /etc/saned.d/epkowa.conf and insert in the network section a line with your Printer's IP address and port number 1865 (i.e. net 192.168.1.210 1865)

then install 4) network plugin

To use the scanner execute program "iscan" from the command line (maybe the menu entry will also work)

---

### Post by pdc on 2013-03-25
glad this all worked;

curiously, Epson say:

**ALWAYS INSTALL** the Data package **FIRST**

[http://download.ebz.epson.net/faq/linux/faq_ls_00002.html](http://download.ebz.epson.net/faq/linux/faq_ls_00002.html)

.............I agree it is well hidden .............

---

### Post by mikerobinson on 2013-05-02
These instructions worked for me for Epson L555 even though it's not listed in the network plugin package's supported devices.

---

