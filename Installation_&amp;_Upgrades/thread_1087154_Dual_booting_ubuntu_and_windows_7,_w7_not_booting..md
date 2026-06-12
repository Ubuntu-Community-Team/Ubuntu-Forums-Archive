---
title: "Dual booting ubuntu and windows 7, w7 not booting."
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Drood on 2009-03-04
Hi, my problem is I can not get windows 7 to boot after installing it. I followed several guides on the internet and in the Ubuntu forums to install windows 7 after ubuntu and then restore grub, so I got GRUB working again but Windows 7 will not boot, I get different errors like "partion does not exist" and other ones referring to windows boot loader not being there.

This is the output of fdisk -l :
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004a004a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3333db0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         392     3148708+   7  HPFS/NTFS
/dev/sdb2             393        9964    76887090    5  Extended
/dev/sdb5             393        7017    53215281   83  Linux
/dev/sdb6            7018        9568    20490876    7  HPFS/NTFS
/dev/sdb7            9569        9964     3180838+  82  Linux swap / Solaris

```


I for some reason have 2 ntfs partitions, 1 is a 3gb one that persisted after installing Ubuntu(overwriting windows vista) the first time a couple of months ago. The other one, a 20 gb partition i created to install windows, I install windows initially and it booted fine, but once i restored grub and added it to the menu.lst it wont boot.

Here is what I added to the menu.lst :
```

title           Windows 7beta (Games)
root            (hd1,5)
makeactive
chainloader +1 

```

This is the layout in Gparted : 
[[IMG]http://img217.imageshack.us/img217/6776/screenshot2.th.png[/IMG]](http://img217.imageshack.us/my.php?image=screenshot2.png)

I cant figure out what am I doing wrong, does reinstalling grub erase windows bootloader? I do not know exactly how OS loading/booting works. If anyone could help me I would greatly appreciate it.Thanks.


Edit : I just rebooted to check for error messages and they are as follows :
When i set root as (hd1,5) thats sdb6 the 20g windows 7 partition I get " partition does not exist"
When I set root as (hd1,0) thats the sdb1 3g partition I get " Error 13: "Invalid or unsupported executable format".

---

### Post by Drood on 2009-05-14
I got this solved a while ago, I was just looking through my threads. Just in-case someone gets here by googling it, I was trying to install Windows 7 after Ubuntu , Windows overran GRUB, it requires you to boot with the live cd and re install grub onto the appropriate partition (I cant recall how to do it, just google it). There is also good guides out there with the whole process.

---

### Post by lindsay7 on 2009-05-14
.  old post

---

