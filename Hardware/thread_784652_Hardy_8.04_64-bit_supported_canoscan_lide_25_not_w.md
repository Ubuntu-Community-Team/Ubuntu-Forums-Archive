---
title: "Hardy 8.04 64-bit supported canoscan lide 25 not working"
date: 2008-05-06
forum: Hardware
---

### Post by dlmoak on 2008-05-06
My canoscan lide 25 scanner will not work.  It is recognized by sane-find-scanner and by scanimage -L.  If I try a command line scan, the light bar never moves and a black image is saved.  If I try scanning from Xsane or Gimp the light bar also never moves and the programs lock up.  I have modified /etc/san.e/plustek.conf by adding the following:

[usb] 0x04a9 0x2220
device auto

Since the bus seems to change when I plug in the scanner the "auto" option seemed best to me.

Any suggestions?  I'm running 64-bit Hardy

---

### Post by dlmoak on 2008-06-01
Oops!  The scanner was broken.  When I connected the new one it worked out if the box.

---

