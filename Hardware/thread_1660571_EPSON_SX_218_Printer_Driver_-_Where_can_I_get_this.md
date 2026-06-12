---
title: "EPSON SX 218 Printer Driver - Where can I get this?"
date: 2011-01-05
forum: Hardware
---

### Post by eljc2 on 2011-01-05
I've been trying to get my laptop running ubuntu to print to an Epson SX 218 all in one printer on a family member's computer over our wireless network.

Ubuntu is able to pick up the printer OK, but does not have SX 218 drivers pre-installed. I tried installing the driver for a similar model, but this just cause the printer to print random blank pages and random text, as well as messing up the print queue.

I've searched on the internet for linux drivers for this printer model, but all the websites that claim to have it want payment!

Anyone know where I could download the right driver?

---

### Post by amunne on 2011-01-09
Hi! I had the same problem and I found a solution. The correct driver for this printer, and for a lot of printers are in this website: [http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

I have Ubuntu 10.10 and it works perfectly!

I write on this because when you're searching for this problem it's the first webpage that it's showed on google. I hope it will help a lot :)

(Excuse me for my poor english, its not my mother language)

---

### Post by eljc2 on 2011-01-10
Thanks for your help ammune.

I have downloaded the driver from that website.

I went through the Add Printer Wizard and selected the ppd file for the Epson Stylus SX218. When I get the the end (window titled 'Describe Printer'), I get this message:

CUPS server error:

There was an error during the CUPS operation: 'server-error-internal-error'.


Any ideas what this could be?

---

### Post by eljc2 on 2011-01-10
Ok, I tried this again and it seems the problem is that the driver is not installed properly. (I got an error saying the filter was not installed).

The manual says to type this in the terminal to install it:

# rpm -i epson-inkjet-printer-<Printer name>-<Version>.<Architecture>.rpm

The file I downloaded was called epson-inkjet-printer-workforce-320-sx218.rpm and I have extracted it.

I tried typing: #rpm -i epson-inkjet-printer-workforce-320-sx218-1.0.0-1lsb3.2.i486.rpm

This doesn't seem to have worked. How can I check if the driver is installed?

What is the alternative way of installing the driver through package manager?

---

### Post by IcarusR on 2011-01-10
You need to download the .deb not the .rpm file. 
Having downloaded it to install double click on it will launch gdebi & you can install it from there.

---

### Post by eljc2 on 2011-01-10
Great...that seems to have done the trick! Thanks guys. Solved!

---

### Post by mrtymek on 2011-05-10
Hello guys. I've got a problem with the device.
The printer actually works out of the box, (ok, some auto download) but I cannot get the scanner to work. I've installed the avasys driver, and the same story again. Printer works, scanner nah.

I'm using 11.04, the device is Epson Stylus SX218, and the software I'm trying to use is ubuntu's default Simple Scan.

> $ sane-find-scanner
found USB scanner (vendor=0x08ff, product=0x2810) at libusb:004:002
found USB scanner (vendor=0x04b8, product=0x0865) at libusb:002:005

$ scanimage -L

No scanners were identified. [...]


---

### Post by amulet on 2011-05-17
I found the drivers for the scan utility for Epson Multifunction inkjet printers here: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo)

After installing the driver and ImageScan! for Epson, Xsane worked perfectly! 

I hope that helps

---

### Post by mrtymek on 2011-05-25
Thanks amulet, I'll try that at home!

---

