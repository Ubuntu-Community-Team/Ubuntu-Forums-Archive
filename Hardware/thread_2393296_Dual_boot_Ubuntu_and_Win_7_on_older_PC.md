---
title: "Dual boot Ubuntu and Win 7 on older PC"
date: 2018-06-01
forum: Hardware
---

### Post by nloxx on 2018-06-01
Hi Everyone,

I've been trying to figure this out, but I'm still very new to linux. I have an old PC that I currently have ubuntu 18.04 and win 7 installed to separate HD's. Currently Ubuntu is my primary drive (0 master) and the win 7 drive is 1 slave I think in the chain. My MB does not support UEFI, and it doesn't even allow me to pick what HD I want to boot from (only option is boot from HD or boot from CD, etc etc)..so like I said, it's pretty old.

Both OS's are installed and are working fine, but having to pop the lid open and switch the drive cables (move the win7 to the 0 master when I want to run win7) is a pain. 

Is it possible to add/modify the grub loader (if I have the term correct) for the linux boot drive so I can get a menu at startup to select which one I want?

What would I need to download to do this?

thanks!

---

### Post by oldfred on 2018-06-01
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Is your second drive in a CD/DVD caddy? Those often are not bootable as hard drive (but still boot as DVD?)
If you have to switch master/slave, you have a system that is so old that it would not support Windows 7. It almost has to have cable select BIOS.

I suspect something wrong with hardware configuration.
Very old IDE drives had tiny pins to select  master/slave. I really hated those, so when SATA was only a few dollars more I converted to SATA drives.

Newer  IDE systems have another pin setting for cable select.
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive. 

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable. 

I did once try to use a DVD cable which was not compatible with cable select and had issues.

---

