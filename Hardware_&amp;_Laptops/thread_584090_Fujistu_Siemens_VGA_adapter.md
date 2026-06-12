---
title: "Fujistu Siemens VGA adapter"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by givotec on 2007-10-20
I installed Ubunto 7.04 on my laptop fujitsu siemens Amilo LA 1703
Everything is working fine except the vga:(
my vga adapter is VIA Chrome9 HC IGP WDDM
I tried 
sudo modprobe VIA Chrome9 HC IGP WDDM
but it gave unknown model
So please anyone can help me?
thanks

---

### Post by gagatz on 2008-01-20
Might come a bit late, but did you try to 
dpkg-reconfigure xserver-xorg
in a terminal?

---

