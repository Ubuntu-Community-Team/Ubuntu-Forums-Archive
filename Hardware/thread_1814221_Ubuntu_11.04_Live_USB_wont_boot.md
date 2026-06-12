---
title: "Ubuntu 11.04 Live USB wont boot"
date: 2011-07-29
forum: Hardware
---

### Post by [RMC]Pip on 2011-07-29
Hi,

on my work laptop ASUS X71SL with SanDisk Ultra Backup (32GB) USB Ubuntu Live USB halts at the booting process.

The last lines on the screens are:
```
EISA: Detected 0 cards
cpuidle: using governor ladder
cpuidle: using governor menu
TCP cubic registered
NET: Registered protocol family 10
NET: Registered protocol family 17
Registering the dns_resolver key type
Using IPI No-Shortcut mode
registered taskstats version 1
```Strange, since I have managed to use it on some other PCs / laptops. I have created the Live USB with Universal USB Installer.

Can someone please give me some hints how could I fix this problem. Thanks!

---

### Post by [RMC]Pip on 2011-07-29
Found this thread: [http://ubuntuforums.org/showthread.php?t=1662577](http://ubuntuforums.org/showthread.php?t=1662577)
It seams to be a problem with ASUS laptops. :mad:

I follow the instructions, but couldn't update grub:
```
sudo update-grub
/usr/sbin/grub-probe: error: cannot stat 'aufs'.
```Any tips! Thx

---

### Post by VeRychard on 2012-04-17
I SOLVED IT!!!!!

If you have an Asus laptop, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)

---

