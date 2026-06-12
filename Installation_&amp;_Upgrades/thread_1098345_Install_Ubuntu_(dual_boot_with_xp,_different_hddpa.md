---
title: "Install Ubuntu (dual boot with xp, different hdd/partition)"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by accused on 2009-03-16
Hello, I'm trying to install Ubuntu on a PC that already has XP installed on a sata hdd (sda in the partition manager during install).  I want to put Ubuntu on a different hdd and partition, and iirc both hdd's are sata while there is also an ide drive hooked up as well.  It's been a while so I can't remember exactly which are which but if this info is required I can take a look.

So far, I've installed twice.. using the default of installing grub to hd0 and then to sda (xp partition) but both give me grub error 22 on reboot after install so I'm wondering if anyone here can steer me in the right direction as I'm obviously not doing it right and all the research I've been trying to do usually point to installing both on the same hdd but different partitions, or to seperate drives but seemingly out-dated methonds that don't apply?

Thanks!

---

### Post by meierfra. on 2009-03-17
I suggest to install Grub to the MBR of the Ubuntu drive and set your Bios to boot from the Ubuntu Drive: 

Boot from the Ubuntu Live CD, open a terminal (Applications->Accessories->Terminal) and type

```
sudo grub 
```

and at the "grub>" prompt.

```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)
Still at the "grub>" prompt:


```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")

Reboot, with the bios set to boot from the Ubuntu drive.

You will also need to edit "menu.lst" to be able to boot to XP. If you would like help for that, post the output of

```
sudo fdisk -lu
```

---

### Post by sahabcse on 2009-03-17
Hi

For fixing the grub follow below url

=================================
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
=================================

Regards,
Sahab

---

### Post by accused on 2009-03-17
Awesome, thank you both.  I've had it working before, but it was after a *lot* of messing around and in the end I had no idea what I actually did right to make it work, so i'll bookmark this for future reference in case I come to this again.

I think I'll be ok with menu.lst, but if not, I'll post the requested output later and again offer my thanks. :)

---

