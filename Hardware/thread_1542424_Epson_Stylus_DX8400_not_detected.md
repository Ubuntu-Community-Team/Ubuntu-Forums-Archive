---
title: "Epson Stylus DX8400 not detected"
date: 2010-07-30
forum: Hardware
---

### Post by NDW57 on 2010-07-30
Hi, I'm new to Ubuntu (and Linux) having used Windows for years (from version 3.1!). I recently installed Ubuntu 10.04 on my PC completely overwriting the previously installed Windows XP. I have an Epson DX8400 All-in-One (scanner/printer/copier) attached to the PC via a printer USB cable. The printer bit works well but when I tried to scan using "Simple Scan" the scanner part wasn't detected. I've got as far as SANE and it would seem that there is an appropriate "back-end" for the scanner function but that's as much as I can work out. What precisely do I need to do/ download/type-in to get the scanner function working. Thanks, Neil

---

### Post by ellgor on 2010-07-31
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit (for your model or nearest) and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly, it will appear in the graphics section or you can run it by Alt+F2 and typing in its name.

Regards, Ellgor.

---

### Post by NDW57 on 2010-08-02
Hi, I've just switched to Ubuntu 10.04 from Windows XP. Unfortunately, although my Epson Stylus DX8400 prints perfectly well, when I try to scan a document using Simple Scan (or Xsane Image Scanner) the PC fails to detect the scanner. I've looked on the internet and there does seem to be something on the SANE website but I haven't got a clue how to proceed from there - I need some precise instructions please. Any help appreciated. Neil.

---

### Post by sisco311 on 2010-08-02
Download and install the driver and the scanner utility from: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Select your printer model, distribution, etc... Then download and install iscan-data_1.0.1-1_all.deb and iscan_2.25.0-1.ltdl7_i386.deb if you are using the 32-bit version of Ubuntu or iscan_2.25.0-1.ltdl7_amd64.deb for the 64-bit version. 

You may need to reboot the computer.

Go to Applications -> Graphics -> Image Scan! to start iscan. But the scanner should be recognized by xsane too.

---

### Post by cariboo on 2010-08-02
Please don't create multiple threads on the same subject. I have merged your two threads.

---

