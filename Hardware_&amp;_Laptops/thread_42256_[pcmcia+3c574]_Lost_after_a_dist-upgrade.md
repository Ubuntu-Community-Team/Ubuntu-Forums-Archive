---
title: "[pcmcia+3c574] Lost after a dist-upgrade"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by 1sy8 on 2005-06-16
Hi all.

I'm on a very old IBM Thinkpad 365XD, that I try to revive with Ubuntu.

I have a few problems with it (I'll come back to them later) but the worst problem came lately. The 3c574 LAN card that I use and the entire pcmcia subsystem was lost   after I dist-upgraded Warty to Hoary !

1- cardmgr says no pcmcia driver in /proc/devices
2- modprobe 3c574cs seems to load the modules but then my interface is still not up.
3- ifup eth0 returns with errors on sit0 and so on ..

What can I do to recover the network connectivity ?

---

### Post by 1sy8 on 2005-06-20
Don't tell me I have to start a brand new install just to make my 3Com card work ???!!

It would be a real pity for a much famed Desktop distro !

---

