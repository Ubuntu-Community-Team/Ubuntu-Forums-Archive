---
title: "changing boot sector !"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by asel_ on 2009-02-20
Hi , I don't know if the title is fit or not . Anyway , I used ubuntu server 8.04 for long time , after my server get full, I bought a new PC to act like server, I installed 2 hard disks, one with ubuntu server ( IDE 80 GB ) and another one is sata (320GB) to hold the files, I partioned the hdds manually, but I can not boot now ,because the boot loader installed on the sata Hdd, while the / folder and boot folder are located in the IDE Hdd , and my pc booting from IDE NOT SATA in default . Now how to install the make the boot sector on the IDE hdd ? Thank you in advance and I hope my post is clear .

---

### Post by caljohnsmith on 2009-02-20
To install Grub to the MBR (Master Boot Record) of the drive that has Grub's boot files (your IDE drive), how about trying this:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how that goes or if you run into problems.

---

### Post by asel_ on 2009-02-20
Thank you for replay, I did what you said , but it still not booting , I tried to make new install of ubuntu , during partitioning it deal with sata hdd as 1st hdd.Anyway,can I choose where to install boot loader during installing ubuntu sever ?

---

