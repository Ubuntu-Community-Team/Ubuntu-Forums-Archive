---
title: "Conexant driver-Inspiron 8200"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by Finncannon on 2006-01-30
I am VERY new to linux/Ubuntu and am reluctant to do things that I don't understand. I've been reading til my eyes are about to fall out! But I still have a question. I've read the dialupHowto wiki.

I've just installed Ubuntu 5.1 in a dual boot mode with XP on a Dell Inspiron 8200. ListModem log is:
================================================== ===================
= SYSTEM INFORMATION =
================================================== ===================
Date : 1/26/2006
ListMdm Ver : 1.6
Windows OS : Microsoft Windows XP
Build Number : 2600

================================================== ===================
= RESULT OF MODEM QUERY =
================================================== ===================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
PCI CONFIGURATION INFORMATION READ:
VENDOR ID : 8086
DEVICE ID : 2486
SUBVENDOR ID : 14F1
SUBDEVICE ID : 5421
REVISION ID : 02

DEDUCED INFORMATION:
VENDOR NAME : ICH
DEVICE NAME : ICH3 (AC '97 MODEM)
SUBVENDOR NAME : ACTIONTEC -- [HTTP://WWW.ACTIONTEC.COM/](HTTP://WWW.ACTIONTEC.COM/)
MODEM TYPE : HSF
WINXP INBUILD SUPPORT : NO

Do I need to follow steps 1 thru 4 of the Conexant driver install procedure if I use the driver you uploaded to the ftp site? And which file would I use? I assume <conexant_192-1ubuntu-1_i386.deb>. Simple is good. Cookbook steps would be great.

Thanks

---

### Post by towsonu2003 on 2006-02-03
did I answer this before? it looks familiar.

anyway. check out the second link in my signature, and use the section about scanmodem tool. once you got your modemdata.txt, read it from top to bottom (reading it about 5 times will help you understand approximately what's going on ;) ). If you can understand which modem you got, refer to the relevant section in the wiki (second link in signature). if you can't, attach (as a file, don't post it as text) the file here and we'll try to make sense of it.

---

