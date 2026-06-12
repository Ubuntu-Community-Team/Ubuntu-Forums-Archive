---
title: "brother dcp 7040 printer works but  the scanner does not work"
date: 2013-09-19
forum: Hardware
---

### Post by claudio5 on 2013-09-19
With lubuntu 13.04 i just installed a brother dcp 7040 printer and it works right but the scanner does not. I tried a lot of issues with no results. I need your help please!

---

### Post by md80hb-iuh on 2014-03-28
I have Ubuntu 12.04, 32 bits, Using CUPS.  Connect your USB DCP7040.

For the scanner:
A)Go on the Brother Web site and download the BRSCAN3 (32 bit version) package and install.
B)Then follow that post (starting  where you have to edit /lib/udev/rules.d/40-libsane.rules as being super user of course till modifying the 50-udev-default.rules file).
[http://ubuntuforums.org/showthread.php?t=1967467](http://ubuntuforums.org/showthread.php?t=1967467)
C) Reboot
Should be able to scan using simple-scan.

For the printer:
A) Use CUPS only. Download  and install package from Brother.
B) Open browser and type in that link [http://localhost:631/admin](http://localhost:631/admin)    Note that you will need to know where the DCP7040.ppd file is (/usr/share/ppd)
C) Adding the printer using the GUI should be a breeze. DO NOT USE THE "Application-> System tools-> System parameter " application. Using the web server will take care of everything.
Good luck.

---

