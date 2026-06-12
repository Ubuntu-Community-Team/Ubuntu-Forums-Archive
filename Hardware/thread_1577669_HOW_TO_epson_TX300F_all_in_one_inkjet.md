---
title: "HOW TO epson TX300F all in one inkjet"
date: 2010-09-19
forum: Hardware
---

### Post by ItalOz on 2010-09-19
This device has scanner and printer functions
to day I installed it on Ubuntu 9.10 on an Asus laptop.

I used the drivers that you can download from
[[COLOR="Red"]Avansys[/COLOR]]("http://avasys.jp/eng/linux_driver/") that releases drivers for Linux for Epson.

Look for the *All-in-Ones (Multifunction Inkjet Printers)*icon
Then on the drop down menu I did not find the 300 model so I selected the 400 and that brought me to a download where between the *Applicable Models* you'll find the *Epson Stylus Office TX300F* model.

I downloaded the [COLOR="Blue"]*epson-inkjet-printer-escpr_1.0.1-1lsb3.2_amd64.deb*[/COLOR] and installed.

Connected the printer and it worked

I tried a few times and I think there is a bug when you select monochrome printing from the options because the text look too big when printed.
The colour print seem to work fine.

The scanner wasn't working from Xsane

So I followed [[COLOR="Red"]this link[/COLOR]]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo")

I downloaded [COLOR="Blue"]*iscan-data_1.3.0-2_all.deb*[/COLOR] and [COLOR="Blue"]*iscan_2.26.0-3.ltdl7_amd64.deb*[/COLOR] in order to install Iscan software.

I have the 64bit Ubuntu, check to download accordingly to your version

All went well and I could launch [COLOR="Blue"]Applications > Graphics > Iscane[/COLOR] that recognised the scanner.

I could also use the Automatic Document Feeder with this software and now also Xsane detects the scanner

Hope it helps

---

### Post by grock58 on 2011-05-12
Your how-to has solved my problem. Thanks for that .

---

