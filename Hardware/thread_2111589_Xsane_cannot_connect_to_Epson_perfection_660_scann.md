---
title: "Xsane cannot connect to Epson perfection 660 scanner"
date: 2013-02-02
forum: Hardware
---

### Post by dtf6 on 2013-02-02
I started Xsane, and get message 

Failed to open device ' snapscan:libusb:004:004':
Ijnvalid argument

I check the Epson Perfection 660 scanner on Win XP and it works fine.
So how to enable it to works on ubuntu 12.04.1

---

### Post by pdc on 2013-02-03
seems like folks have been installing this scanner for some time on Ubuntu:

I googled on 

> ubuntu solved epson perfection 660 scanner

and got various links from 2008 onwards ..

from sane

[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

for the 660, it shows good support

> Perfection 660 	USB 	0x04b8/0x0114 	Good 	  	SnapScan
(1.4) 	sane-snapscan

this link

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson)

suggests you need to edit a file and it would seem the command to open the file is

> gksudo gedit /etc/sane.d/snapscan.conf

and it quotes a link you should read

[http://ubuntuforums.org/showthread.php?p=6798088](http://ubuntuforums.org/showthread.php?p=6798088)

.......post #2 seems to have some pertinent details

.....post back as needed for more help ..........

---

### Post by dtf6 on 2013-02-03
Thanks pdc.

I just follow [jarondl]("http://ubuntuforums.org/member.php?u=84222")'s post from [http://ubuntuforums.org/showthread.php?p=6798088](http://ubuntuforums.org/showthread.php?p=6798088)
and solved my problem

---

### Post by pdc on 2013-02-03
great; welcome to Ubuntu and enjoy!

........oh....if you edit the title and add SOLVED it pleases the forum administrators and will help any others following in your wake

best wishes

---

