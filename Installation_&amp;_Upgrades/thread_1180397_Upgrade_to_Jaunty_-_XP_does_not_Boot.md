---
title: "Upgrade to Jaunty - XP does not Boot"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by gmgj on 2009-06-06
(My first and only) automatic upgrade from intrepid to jaunty.
I thought I was safe, I had a version of my GRUB menu.lst saved as menu.lst.jic (in grub dir)

Its gone  (**did it get saved someplace else?**)

Here are my two disks.  I had an old XP machine.  I added a new (sda) 500 gig drive and partitioned  it as follows when I added ubuntu:
I left the orginal (sdb) disk alone.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd5aaa9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       24935   200282355    f  W95 Ext'd (LBA)
/dev/sda2           24936       51044   209720542+   7  HPFS/NTFS
/dev/sda3           51045       57572    52436160    7  HPFS/NTFS
/dev/sda4   *       57573       60801    25936942+  83  Linux
/dev/sda5               2         523     4192933+  82  Linux swap / Solaris
/dev/sda6             524        1045     4192933+   6  FAT16
/dev/sda7            1046       24935   191896393+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3047f66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

So I  sudo gedit /boot/grub/menu.lst 

and try this and variations of this (see the lines marked + changes)
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)

...
+savedefault
+savedefault=true
+chainloader	+1

[B]Do I need a map statement ?  
[/B]


If it helps
I can see my XP and Ubuntu files fine.  
I had done a menu.lst where I put XP first as the default.

:popcorn:

---

### Post by gmgj on 2009-06-06
I added 


title		Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


It seems to work.  XP boots by default and I can boot jaunty, 

If anyone sees something wrong, please let me know.  BTW this is so Windows can think its first.



->the rest

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d7a94eb0-3fff-4b8c-896c-a2ffc4b6c0ed
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian

---

### Post by presence1960 on 2009-06-06
Looks good. I would take out the makeactive line though. A lot of people use savedefault and makeactive in their windows entry but really is not necessary.

---

