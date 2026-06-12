---
title: "ubuntu 9.10 upgrade hangs during boot"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by JHCKX on 2009-11-01
I've updated Ubuntu 9.04 to 9.10 today but now I can't boot into Ubuntu. If I choose Ubuntu 9.10 - recovery mode, my computer hangs at:

[5.103556] Clocksource tsc unstable (delta = -2940379007 ms)

Disk activity stops, the only thing to do is a hard reboot.

On a regular boot, the computer hangs after Grub shows

Boot from (hd0,4) ext3 48....
Starting up  . . .

Any suggestions on how to fix this?

---

### Post by JHCKX on 2009-11-02
This is a very strange problem. I discovered by accident that my computer would boot if I connected a usb hub with a mouse and keyboard attached. Without that hub the same problem kept occurring. But even when I could boot the system was unstable. There were a couple of disk checks, some errors were corrected. Even then programs would just freeze. So I did a clean re-install, at least the computer boots normally now. Still to early to tell if the system is stable thoug

---

### Post by zey on 2009-11-02
i recommend you to do a fresh install.

just dont forget to backup your data.

---

### Post by JHCKX on 2009-11-02
Bad news. I'd done a clean re-install yesterday and it seemed to work but today I can't boot. Looks like I'll have to re-install 9.04

---

### Post by zey on 2009-11-03
maybe you need to look over your BIOS setting.
see if your disk boot in IDE or AHCI mode.
mine is using IDE.

its just same as if you using windows XP and Vista.
XP won't boot in AHCI mode. XP boot in IDE mode.
Vista won't boot in IDE mode. Vista boot in AHCI mode.

good luck.

---

### Post by bearlord on 2009-11-29
Hi, I am new in this forum and i've been having exactly the same problem... My computer freezes at startup after grub, and if i try to go on recovery mode i get the clocksource error... 

However, it starts normally if I connect usb devices... I tried reinstalling and I get the same problem, seems that the only way to get it started is by conencting a device to several usb ports.

---

### Post by blahfod on 2010-02-02
I am having this exact problem, anyone find a solution???
blahfod

---

