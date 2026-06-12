---
title: "Triple boot-MSDOS, Vista, Ubuntu help"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Genises on 2009-02-18
Hi everyone,

I know this question may have been asked already but I can't seem to find here on the forum. I am trying to setup a laptop with a Multi boot. I want to be able to switch between Ubuntu, Vista, and MS DOS. I currently have all three installed on the machine and I am able to switch between Ubuntu and Vista. However I do not get the option for the MS DOS with is located in the first partition. I think but not sure when I loaded the Vista it may have altered the MBR causing DOS not to be seen by Ubuntu when I loaded it. Any way suggestion or instruction anyone?  Thanks

---

### Post by fopetesl on 2010-03-11
Ah, Ha! Genises. I have almost exactly the same problem :cry:
Except my layout is slightly different.
I partitioned the disk into:```
/dev/sda1 WIN95 FAT32 C:\ with DOS 7.1 installed 1st and checked OK
/dev/sda2 LINUX ext4 /boot
/dev/sda3 NTFS D:\ WIN XP installed 2nd and checked OK
/dev/sda4 Extended
/dev/sda5 LINUX ext4 / UBUNTU installed last and checked OK
/dev/sda6 LINUX ext4 /home
/dev/sda7 LINUX swap
/dev/sda8 LINUX ext4 /tmp
```
And similarly I can choose to boot into Ubuntu or XP but there is no DOS 7.1 choice.

Maybe if I can discover the correct (sd0,1) or whatever I could hack Grub directly but how to discover the correct parameters?

---

