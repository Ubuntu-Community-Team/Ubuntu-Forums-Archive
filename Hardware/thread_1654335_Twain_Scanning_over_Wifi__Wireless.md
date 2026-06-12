---
title: "Twain Scanning over Wifi / Wireless"
date: 2010-12-28
forum: Hardware
---

### Post by andy_spoo on 2010-12-28
I have an Epson Stylus Photo PX710W.

Does anyone know if it's possible to scan images to a pc / laptop over wifi using Ubuntu?

Works in Windows OK.

Printer driver for Linux can be found here:- 

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

---

### Post by davidmohammed on 2010-12-28
yes - works fine... with a tweak.

download and install the iscan drivers for the px710w from here

then edit the file /etc/sane.d/epkowa.conf

at the bottom of the file you should have a line entry that looks like mine

net 192.168.1.248

i.e. you need to define the printer with a fixed IP address

then you'll be able to use the epson scanner software installed to Applications - Graphics - Image scan for Linux

---

### Post by bonestonne on 2010-12-28
I have my Epson Workforce 600 set up over my network using Wifi, with static IP (reserved in the Router).

Ubuntu 10.10 automatically set it up in Simple Scan, and it works great on my laptop and desktop, no tweaking on my end.

---

### Post by andy_spoo on 2010-12-29
I had a bit of  a problem because I'm using the 64 bit version of Ubuntu, but after a bit compiling and using the old thread here:-

http://webcache.googleusercontent.com/search?q=cache:eXpO5Obpai8J:ubuntuforums.org/showthread.php%3Ft%3D576594+pipslite+amd64&cd=1&hl=en&ct=clnk&gl=uk"

everything is working now. 

Thanks.

---

