---
title: "Compaq Presario V6000 Notes"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by yurtboy on 2007-02-14
Maybe this will help someone set it up.  Though I have not tried NVIDIA
Attached are my
/etc/modprobe.d/blacklist
/etc/X11/xorg.conf --> did not try the real nvidia drivers yet.  Also has touchpad off included
/boot/grub/menu.lst
/etc/modules

Ndis drivers for the wireless are found at the site of 
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en)

Ndiswrapper I downloaded from their site and installed per their directions then all was well.
Remember the make uninstall

Overall it was not that bad.  Once I got the grub pre commands setup right.

---

### Post by ClydeFortna on 2007-05-18
:D  This fixed my erratic boot and my graphics resolution on my V6000.  I also added assign-bus to menu.lst.  Don't know what it might help with.  Waiting to try real NVidia drivers.

 Thanks, Clyde

---

### Post by yurtboy on 2007-05-19
Great!!
Now I am running Feisty and alot has improved.

---

