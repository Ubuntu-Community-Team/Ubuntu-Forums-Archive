---
title: "Holux GR-236 Driver Installation"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by schapman43 on 2007-11-06
You'll have to excuse me.  I am completely new to Linux but I have to say it has renewed my interest in computers!  Anyway, I just installed Kubuntu 7.1 and need to install the drivers for my Holux GR-236 GPS Receiver.  The GPS Device connects to the PC through a USB to serial cable.  Holux does provide Linux drivers but I have no clue how to use them.  

The drivers are located here
[http://www.holux.com/JCore/en/support/DLF.jsp?DLU=http://www.holux.com/JCore/UploadFile/7875498.zip](http://www.holux.com/JCore/en/support/DLF.jsp?DLU=http://www.holux.com/JCore/UploadFile/7875498.zip)

The zip file contains the following files.
Makefile
pl2303.c
pl2303.h
readme.txt
usbserial.c
usb-serial.h

The txt files contains the following.
Release Information

Driver Version for Linux 2.4.x : V0213

Released date: 02/13/2002

Files Included in This Release:
	pl2303.c
	pl2303.h
	usbserial.c
	usb-serial.h
	readme.txt
	makefile
		
Changes in This Release:
	1. To fixed using cat command  problem in Linux


Any help would be appreciated and remember I'm a newby and you cannot assume I know anything :)

---

### Post by netvampire on 2008-01-02
try 

open a terminal, use the 'cd' command to navigate to the directory where the drivers are located. Then type 

```

make
sudo make install

```
'
hopefully that will get you going. good luck.

---

