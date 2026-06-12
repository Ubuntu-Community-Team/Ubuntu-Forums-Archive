---
title: "Dual Boot issue"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by eulallia1 on 2008-12-29
I recently installed Windows Vista, and (while installing accidentally wiped my ubuntu install, but, did not install vista over it's partition).

I used the live CD in order to install to a 20 GB partition, the only problem with the install is it stops at around 95% due to grub not installing properly. When I boot, I do not get GRUB, I get some message saying "Setting up GRLDR" or something, then a barrage of text, then Starting Windows Vista...

I'm currently on the live CD, and wish to have GRUB installed and brought up with a UI on boot like it used to be.

I've tried installing multiple times to no avail, in any place, mostly getting file not found errors when using grub's shell.

Here is some partition information (from the perspective of the live CD):
(GParted)
Name     Format Size      Used   Flags
/dev/sda        149.05 GB 
/dev/sda1 fat32 4.88GB    3.57GB       (Made when I had XP, no purpose now)
/dev/sda2 ntfs  71.84GB   61.95GB boot (Vista Ultimate)
/dev/sda3 ext3  20.98GB   2.41 GB      (Ubuntu 8.04 Hardy)
/dev/sda4 extended51.53GB ---          (Dedicated for holding games for Vista)
   /dev/sda5 ntfs 51.53GB 9.94 GB      (Same as Above)

I'm not completely sure whether or not it is installed on /dev/sda3

---

### Post by 2hot6ft2 on 2008-12-29
Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

---

### Post by eulallia1 on 2008-12-29
> **2hot6ft2 said:**
> Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.
```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 

```
Also, I'm running on the live CD still, using GParted to switch my boot partition from Vista to Ubuntu causes a Can not find OS error on boot

---

### Post by eulallia1 on 2008-12-29
Bumping

---

