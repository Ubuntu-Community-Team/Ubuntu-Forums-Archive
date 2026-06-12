---
title: "Epson Expression Premium XP-800 AIO"
date: 2013-01-11
forum: Hardware
---

### Post by capemayal on 2013-01-11
OS - Ubuntu 12.04 LTS 64-bit
 
Just purchased this unit. On W7 it works fine - not one problem.
 
The unit is wireless and is seen by Ubuntu.
 
Wireless flat-bed scanning works as expected.
 
Using the ADF causes AIO to crash, along with the scanning (xsane or simple scan, either one).
 
I've searched all through the forums and google, to no avail.
 
Any help appreciated.

---

### Post by pdc on 2013-01-13
I am not clear from your post which drivers you are using;

from the Epson site, 

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18782&DSCCHK=1656158aae493417d004b0d5801c13d672b30c9a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18782&DSCCHK=1656158aae493417d004b0d5801c13d672b30c9a)

I see there are debian package drivers for your printer

for 64bit there is the [COLOR="SeaGreen"]epson-inkjet-printer-201208w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

If you don't have this installed, perhaps you do install the appropriate one and see how things go; Epson, like Canon and Brother, provide good linux support, as does HP

---

### Post by capemayal on 2013-01-13
Thanks for the info, I didn't see those before.

Are they just for the printer, or the scanner too?

The printer is working great, it's just  the scanner ADF function, crashes everything.

---

### Post by pdc on 2013-01-13
not sure which drivers you are running ......

.....if I go here......

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and enter your printer, I get to here for the scanner

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631)

at the bottom of the page are listed various packages

Epson say to install the data package first 

[COLOR="SeaGreen"]iscan-data_1.20.0-1_all.deb[/COLOR]

then .... [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_amd64.deb[/COLOR]

you can see there are [COLOR="DarkOrchid"]ltd3[/COLOR] and [COLOR="Magenta"]ltd7[/COLOR] packages......

[COLOR="DarkOrchid"]ltd3[/COLOR] is for old kernels, so you use [COLOR="Magenta"]ltd7[/COLOR]

If you do not have these two packages installed, I suggest you install them in the order I mention above, as that is what Epson advise

[http://download.ebz.epson.net/faq/linux/faq_ls_00002.html](http://download.ebz.epson.net/faq/linux/faq_ls_00002.html)

..........both packages should be easily installed by gdebi installer

---

### Post by w1tebear on 2013-05-23
I am also attempting to do wireless scanning from my Epson XP-800. I have installed the print driver (wireless printing works fine) and the iscan-data and iscan packages. Wired scanning with a USB cable works but I still cannot get wireless scanning to work. Has anyone been able to get this to work?

---

