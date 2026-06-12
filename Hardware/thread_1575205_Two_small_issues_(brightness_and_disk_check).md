---
title: "Two small issues (brightness and disk check)"
date: 2010-09-15
forum: Hardware
---

### Post by dyslexicfurby on 2010-09-15
I have a Toshbia satellite laptop, and the latest iteration of Ubuntu. I have 2 small problems that aren't really interfering with my using it.

1. The brightness is permanently at its lowest setting and cannot be adjusted, either by terminal, shortcut keys, or the brightness app. I've gotten used to this so its not that big a deal.

2. Ubuntu checks my hard disks for errors at boot every 30 boots or so. How can I lengthen this to 60 boots or more?

---

### Post by arrange on 2010-09-15
2. Look at *tune2fs* and its **-c** parameter, for example```
sudo tune2fs -c 60 /dev/sda4
```

---

### Post by dyslexicfurby on 2010-09-16
I think that worked. I won't know until another 60 boots or so. However I was /dev/sda1 not /dev/sda4

Also, although the command worked, there are no "sda*" folders in my /dev/ folder when browsing with the file manager. Could they be hidden?

Thank you

---

### Post by arrange on 2010-09-16
Post```
sudo fdisk -l
ls /dev/[sd]d*
```please.

---

### Post by dyslexicfurby on 2010-09-21
Sorry it took so long.

```
schrodinger@move-along:~$ sudo fdisk -l
[sudo] password for schrodinger: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4058ba0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29698   238549153+  83  Linux
/dev/sda2           29699       30401     5646847+   5  Extended
/dev/sda5           29699       30401     5646816   82  Linux swap / Solaris
schrodinger@move-along:~$ ls /dev/[sd]d*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb
schrodinger@move-along:~$ 

```

Also, my brightness still isn't working.

---

### Post by arrange on 2010-09-21
All looks exemplary :)

For the brightness issue I would suggest starting a new thread, with detailed info about your laptop type.

---

