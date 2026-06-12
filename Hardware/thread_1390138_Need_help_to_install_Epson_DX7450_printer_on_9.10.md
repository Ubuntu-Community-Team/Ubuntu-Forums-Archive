---
title: "Need help to install Epson DX7450 printer on 9.10"
date: 2010-01-25
forum: Hardware
---

### Post by trevorlewis on 2010-01-25
I have installed Ubuntu v 9.10 on my Gateway PC. Although I have many years experience of PCs using Windows etc., this is my first Linux installation. I would appreciate some help in installing and configuring my Epson DX7450 all-in-one printer. It is directly connected via USB to the computer. 
I have no idea where to start.
 
Edited: please ignore this post. The printer is now working, whereas it was not detected before. It's my guess that it may be related to the fact that I installed the 219 or so updates that Ubuntu reported as being available. Whatever, I'm now a happy bunny.....

---

### Post by weiersc on 2010-02-22
The problem I have is that the printer is recognised, but I cannot get the scanner to work. I was able to get the scanner to work under 9.04, but under 9.10 it does not. Xsane just tells me that there are no devices available even though the command sane-find-scanner shows the device, and /etc/sane.d/epson.conf has the device specified.

---

### Post by weiersc on 2010-02-22
Update:

I finally found a driver at [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)  (I specified the Epson DX7400 printer) - It installs a little programme, called ImageScan, which provides a simplified means to scan. Xsane also works after that.

---

