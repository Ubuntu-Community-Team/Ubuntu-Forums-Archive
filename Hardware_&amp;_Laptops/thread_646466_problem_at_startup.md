---
title: "problem at startup"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by sdm on 2007-12-21
My laptop is a lenovo y500 with both ubuntu fiesty and windows xp, very frequently after booting at the login page where it asks the username, it refuses to take entry from the keyboard:( and the mouse is also blocked!!:confused: extremely frustrating,:mad: the only way is to do a reboot!!!#-o

---

### Post by rmsrohan on 2007-12-23
had the same prob but after lots of googlin found that adding 

locale=fr_FR i8042.reset to your kernel line solves the problem with no error on sound or others


eg: 

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.22-14-generic ro quiet splash locale=fr_FR i8042.reset
initrd /boot/initrd.img-2.6.22-14-generic
quiet

---

