---
title: "URGENT! bootmgr is missing"
date: 2008-11-14
forum: General Help
---

### Post by Axel-P on 2008-11-14
I'm not sure what i did wrong, but after reboot my grub doesn't want to load, last time i had problems with the grub i solved the problem reintalling the boot loader with a mandriva powerpack dvd but not it says "could not find root devie :-( guessmounts failed at usr/bin/install_bootloader line 28", but after this error it rebooted and now my grub is gone XD, so i can acces windows vista but not Ubuntu

---

### Post by caljohnsmith on 2008-11-14
When you say you can access Vista, do you mean access the partition from your Mandriva DVD? If you are getting a "bootmgr missing" I assume you can't boot into Vista? How about opening a terminal and posting:
```
sudo fdisk -lu
```
Also, how about trying the following to restore Grub to the MBR:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And please post the output of all the above commands.

---

### Post by Axel-P on 2008-11-14
Thank but my partition tables are all screw up, i have to reinstall ubuntu (and i dont know why but mandriva told me that he wasnt able to reinstall the windows boot but it did it anyways xD)

---

