---
title: "did I wiped out my XP?"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by attilab on 2009-03-07
today finisdhed the new ubuntu [installation]("http://ubuntuforums.org/showthread.php?t=1089828"), want to boot in to XP and not working.
how can I check if the XP is still alive, but just me unable to boot it?
help

---

### Post by Partyboi2 on 2009-03-07
Open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo fdisk -l
``` this should tell if you windows partition is still there.

---

### Post by attilab on 2009-03-07
what and how me to read this:

attilab@attilab-laptop:~$ sudo fdisk -1
[sudo] password for attilab: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
attilab@attilab-laptop:~$

---

### Post by amauk on 2009-03-07
Little L, not a one :D

---

### Post by attilab on 2009-03-07
ye, this is a different story,
remember doing it to sda6, but what now? need education on this,
still alive?
attilab@attilab-laptop:~$ sudo fdisk -l
[sudo] password for attilab: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d936d93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       14592    76252522+   f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686    7  HPFS/NTFS
/dev/sda6           10199       14592    35294773+  83  Linux
attilab@attilab-laptop:~$

---

### Post by taurus on 2009-03-07
> **attilab said:**
> ye, this is a different story,
remember doing it to sda6, but what now? need education on this,
still alive?
attilab@attilab-laptop:~$ sudo fdisk -l
[sudo] password for attilab: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d936d93

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Blue"]/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS[/COLOR]**
/dev/sda2            5100       14592    76252522+   f  W95 Ext'd (LBA)
**[COLOR="Blue"]/dev/sda5            5100       10198    40957686    7  HPFS/NTFS[/COLOR]**
/dev/sda6           10199       14592    35294773+  83  Linux
attilab@attilab-laptop:~$

Looks like good news.  You still have two ntfs partitions and your windows is probably on /dev/sda1.

Install ntfs-config and use it to configure and mount your windows if you want.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

And if you are having problems booting windows, post your /boot/grub/menu.lst.

```
cat /boot/grub/menu.lst
```

---

### Post by attilab on 2009-03-07
i did the directed install, but actually it was there,
at the boot prompt I select XP, but just blinks and gets back to boot selection,
now, this is what I have, I guess the same as before the command install ntfs-config:
please tel me more, I need to get back to XP asap...


## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		cf23a85a-e603-48db-a8ad-24ad785735ea
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf23a85a-e603-48db-a8ad-24ad785735ea ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cf23a85a-e603-48db-a8ad-24ad785735ea
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf23a85a-e603-48db-a8ad-24ad785735ea ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cf23a85a-e603-48db-a8ad-24ad785735ea
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf23a85a-e603-48db-a8ad-24ad785735ea ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cf23a85a-e603-48db-a8ad-24ad785735ea
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf23a85a-e603-48db-a8ad-24ad785735ea ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cf23a85a-e603-48db-a8ad-24ad785735ea
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

attilab@attilab-laptop:~$

---

### Post by attilab on 2009-03-07
please help me log in to XP, need to pick my staff............

---

