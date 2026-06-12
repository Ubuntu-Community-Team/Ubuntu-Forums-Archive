---
title: "Brother DCP-130C + Ubuntu 8.04= ???"
date: 2008-07-11
forum: General Help
---

### Post by thomashome on 2008-07-11
I have a Brother DCP-130C printer. Ubuntu seems to find it but it does not work. When I select it then press print I look at my printers screen and it says "Receiving Data" then nothing happens. And goes back to doing nothing with just "100% Normal 01" on the screen as when you turn it on. The Printer is USB.

Yelp and this forum has never had a post like this!

---

### Post by avtolle on 2008-07-11
Have you installed the driver yet? See this link [https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(Brother](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(Brother)) about obtaining the correct driver for your printer from the repositories (I believe the one you need is the one with bh7 in the name). Install the driver(s), then see what occurs.

---

### Post by TopEnder on 2008-07-12
Hi,

You do not mention what version of Ubuntu are using (32bit or 64bit) anyway the following Posts give a very good description of How To
Ref #1 - [http://ubuntuforums.org/showthread.p...other+printers](http://ubuntuforums.org/showthread.p...other+printers)

Ref #2 - Also look in System/Adminstration/Synaptic Package manager (Ubuntu). You may find the following packages for your DCP130C
brother-lpr-drivers-bh7
brother-cups-wrapper-bh7
If these packages are there, Un-install what you have already installed (trying to get the DCP130C working) and use these packages to get the printer side of the DCP130C working.
If the packages are not there then follow the posts in Ref #1 Make sure the Printer is diconnected from the power and the USB cable is disconnected for both solutions.
As yet there are no drivers for the Scanner side of the DCP130C, so you need to follow the scanner direction in Ref #1. there is some very goog information within the Post but you will need to read through all the posts in Ref #1 and maybe download (save) for reference, until you are up printing and scanning. 

There is another post (recently) re: Brother DCP130C and following the above it appears he got his Brother DCP130C printer working.

---

