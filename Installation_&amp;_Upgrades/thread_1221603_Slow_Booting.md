---
title: "Slow Booting"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by Alasta on 2009-07-24
Hello 

I have an old PC ( Pentium 3 512mb ram 10gb disk ) on which I previously havw installed xubuntu 9.04 This takes 10 minutes to start and runs very slowly indeed ,yet the previous version was perfectly usable . 

My intention is to use this PC connected to my Hi Fi to use for music , possibly to run spotify .


Many thanks

Alastair

---

### Post by kdetech on 2009-07-24
See [http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[http://www.salatti.net/tweak-ubuntu-for-speed](http://www.salatti.net/tweak-ubuntu-for-speed)

My advice reinstall xubuntu with alterneate cd on ext2 filesystem and give 2 gb swap. 
Configuring swapiness

If you have 512 mb ram turn of swappiness
with ALT+F2
gksudo mousepad /etc/sysctl.conf
Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:
vm.swappiness=0

If you have less than 512mb I advice
vm.swappiness=25

---

### Post by kerry_s on 2009-07-24
try a different distro with xfce4.

i'm using debian testing xfce4 on 450mhz 256mb ram, no problems here.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/)

xfce4 is in the advanced desktop menu, theres also lxde if you want to try lighter, i've never had lxde work right for me but you might have better luck.

i recommend a base install build up, with only what you want.

---

### Post by Alasta on 2009-07-26
Thanks for your help . I have gone with the older 8.04 , which incidentally runs spotify just fine .:D

---

