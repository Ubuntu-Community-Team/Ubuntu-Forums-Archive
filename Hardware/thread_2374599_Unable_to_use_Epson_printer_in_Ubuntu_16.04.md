---
title: "Unable to use Epson printer in Ubuntu 16.04"
date: 2017-10-17
forum: Hardware
---

### Post by gordie692 on 2017-10-17
just reinstalled 16.04 on my desktop and bought a new epson XP-330 went to web site installed drivers through software center and there were 2 drivers to install did them both added the printer in system settings but won't print or scan

---

### Post by slickymaster on 2017-10-17
Thread moved to **Hardware** for a better fit and thread title edit

---

### Post by pdc on 2017-10-17
so Gordie if I was looking for a driver for the XP-330 I would start here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and entering XP-330 would take me here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=66158&DSCCHK=6049bc668cab7aeb6950ca4f1fedeab58ea5b1a0](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=66158&DSCCHK=6049bc668cab7aeb6950ca4f1fedeab58ea5b1a0) and if you have 64bit ubuntu, you would download epson-inkjet-printer-escpr_1.6.17-1lsb3.2_amd64.deb 

so ```
dpkg -l epson-inkjet-printer*
``` should give something like > [COLOR="#0000FF"]epson-inkjet-printer-escpr_1.6.17-1lsb3.2[/COLOR]         ........ do you get that? and if you go the PRINTERS folder; right-click on the only?? icon for the XP-330; select PROPERTIES 

look in MAKE & MODEL ............ drag the window to the right to see all the text ........ does it say > [COLOR="#0000FF"]epson-inkjet-printer-escpr_1.6.17-1lsb3.2[/COLOR]?

________

how is this printer connected? If usb, what does ```
lsusb
``` give please in a terminal and what does ```
lpinfo -v
``` also give from a terminal please?

---

### Post by strixtux on 2017-10-19
I used to have similar problems with EPSON printers - until I connected them directly with the computer and not over a USB hub.

---

