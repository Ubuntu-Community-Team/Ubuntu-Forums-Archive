---
title: "remove opensuse but keep grub"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by cv65user on 2009-05-30
i have aspire one  with following

c:\ xp + wubi
osx leapord
d:\ vista
knoppix
opensuse
linux swap

but now i need the space back on my laptop as 160gb fill up! lol.
so i deleted opensuse partition and linux swap parition but then i got ntdlr missing, but luckily i had ghost images of each partition so i restored it then grub loader came back. therefore my grub resides on the openesuse partitoin as if i remove the opensuse partition , it obviously removes grub so i get ntdlr missing, press ctrl alt del on reboot . 

if i do 
sudo grub
grub> find /boot/grub/stage1
returns (hd0,6) which is my opensuse installtion
grub> root (hd0,6) - in my case 
grub> setup (hd0)
i also get the green interface grub loader back (as insatlled by opensuse)

so i thought about defaulting to win xp boot loader with fdsik, fixboot, fdisk /mbr then manual instsall grub but all  the fdsisk/fixboot commands said wrote success but evry time i reboot it just came back to ntdlr missing error mesage .

so how do i install grub to mbr of the hdd rather then the partition ?

---

### Post by Mark Phelps on 2009-05-31
> **cv65user said:**
> 
so how do i install grub to mbr of the hdd rather then the partition ?
Basically, you can't -- not completely.  

You can install part of GRUB to the MBR, to be sure.  But, you will then have to install the stage 1.5 and stage 2 files as well as the boot/grub directory with menu.lst file to some partition on the hard drive.

So, at some point, GRUB will have to be "installed" to a partition.

I know it can't be done to an NTFS partition; I've read conflicting reports about it being done to a FAT32 partition.  It certainly can be done it to its own partition or to one formatted for Linux.

---

### Post by cv65user on 2009-06-02
darn , ok in that case i need to remove grub boot loader then i remove open suse (as its currently installed to that partition) and re use windows boot loader as wubi has its own bootloader in windows boot loader  .

as last time i removed the open suse paritiotn i got ntdlr is missing press ctrl alt del  problem

pls can you advise ?

---

