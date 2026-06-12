---
title: "USB Keyed Ubuntu boots on office PC but not on home pc ?"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-10-17
**READ CARREFULLY AS I UPDATE THIS THREAD OFTEN**

I have installed Kubuntu 8.10 on my USB key (8Gb Rally OCZ). It is a persistent usable O/S.

At the office, I have no problems booting with it as it has its own Grub on it.

At home, on my multi boot, booting with the key does nothing. It just goes through the PC Grub instead. I have the USB Key enabled as first boot device. 

If I go into Grub and try to manually boot off of my USB key, I get either errors below (depending on how I attempted it):
Grub Error 11
Grub Error 24

Any suggestions as to what I should do to enable booting directly from that USB key ?

[B]added comments ...
I have no problems with any O/S on my Home PC. I boot to any of them[/B]

**From the Live Kubuntu 9.04 CD** (had mounted the USB key as /usb):
> ubuntu@ubuntu:/usb/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=73fab218-de73-47ad-a1f6-2b3d849d4c3d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=51668974-02d2-4212-8ca6-c5deceaf8f6c none swap sw,pri=253 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda2
UUID=1529e151-364f-407a-b6b9-3ee6841ea79c none swap sw,pri=254 0 0
# /dev/fd0
/dev/fd0        /media/floppy0  vfat rw,user,noauto   0       0
# /dev/sda3
UUID=a6ece3dd-73a6-4ae9-8a1f-f721ac128c7d /PC ext3 relatime,errors=remount-ro 0 1

ubuntu@ubuntu:/$ blkid
/dev/sdc1: LABEL="Office Linux" UUID="73fab218-de73-47ad-a1f6-2b3d849d4c3d" TYPE="ext2"
/dev/sdc2: UUID="51668974-02d2-4212-8ca6-c5deceaf8f6c" TYPE="swap"

ubuntu@ubuntu:/$ fdisk -l

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         843     6771366   83  Linux
/dev/sdc2             844         974     1052257+  82  Linux swap / Solaris

ubuntu@ubuntu:/$ cat/usb/boot/grub/menu.lst
...
## ## End Default Options ##

title           Ubuntu 9.04 (PC)
root            (hd1,2)
chainloader     +1

title           Ubuntu 8.10, kernel 2.6.27-14-generic
uuid            73fab218-de73-47ad-a1f6-2b3d849d4c3d
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=73fab218-de73-47ad-a1f6-2b3d849d4c3d ro quiet splash
initrd          /boot/initrd.img-2.6.27-14-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid            73fab218-de73-47ad-a1f6-2b3d849d4c3d
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=73fab218-de73-47ad-a1f6-2b3d849d4c3d ro  single
initrd          /boot/initrd.img-2.6.27-14-generic

title           Ubuntu 8.10, memtest86+
uuid            73fab218-de73-47ad-a1f6-2b3d849d4c3d
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
chainloader     +1


grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82

/dev/sda is my primary 80Gb HD
/dev/sdb is my second 250Gb HD
/dev/sdc is my USB key plugged in


sudo xxd -l 2 -p /dev/sda
eb48

sudo xxd -l 2 -p /dev/sdb
1000

sudo xxd -l 2 -p /dev/sdc
eb48

sudo xxd -s 1049 -l 2 -p /dev/sda
05ff

sudo xxd -s 1049 -l 2 -p /dev/sdc


With the LIVE CD, it finds the stage1 file on my USB but if I go without the LIVE CD, it does not find it

grub> find /boot/grub/stage1
 (hd0,0)


sudo fdisk -lu

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28842883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381    7  HPFS/NTFS
/dev/sda2        31439205   160055594    64308195    f  W95 Ext'd (LBA)
/dev/sda5       118109880   160055594    20972857+  83  Linux
/dev/sda6        76164228   118109879    20972826   83  Linux
/dev/sda7        31455333    76164164    22354416   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000782bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     8385929     4192933+  82  Linux swap / Solaris
/dev/sdb2         8385930    71300490    31457280+   7  HPFS/NTFS
/dev/sdb3        71312535   176152724    52420095    b  W95 FAT32
/dev/sdb4       176152725   490223474   157035375    f  W95 Ext'd (LBA)
/dev/sdb5       176152788   226484369    25165791    7  HPFS/NTFS
/dev/sdb6       226484433   276816014    25165791   83  Linux
/dev/sdb7       276816078   329187914    26185918+  83  Linux
/dev/sdb8       486303678   490223474     1959898+   7  HPFS/NTFS
/dev/sdb9       350152803   371117564    10482381   83  Linux
/dev/sdb10      329187978   350152739    10482381   83  Linux
/dev/sdb11      371117628   379503494     4192933+  82  Linux swap / Solaris
/dev/sdb12      387889488   486303614    49207063+  83  Linux
/dev/sdb13      379503558   387889424     4192933+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    13542794     6771366   83  Linux
/dev/sdc2        13542795    15647309     1052257+  82  Linux swap / Solaris


---

### Post by Browser_ice on 2009-10-17
xxx

---

### Post by Browser_ice on 2009-10-17
[B]CARREFULLY READ ALL REPLIES IN THIS THREAD TO GET THE FULL VIEW OF THIS PROBLEM
[/B]

Ok, now I booted with the USB Keyed Ubuntu 8.10 in and with no Live CD (in other words, the normal PC Boot).  That grub was installed by my last O/S being Ubuntu 9.04

**Once in the grub, I tried the followings:**
> root (
   Possible disks are : fd0, fd1, fd2, fd3, fd4, fd5, fd6, fd7, hd0, hd1



root (fd0,

Error 24: Attempt to access block outside partition

Possible partitions are:
   Filesystem type is ext2fs, partition type 0x83
   Filesystem type is unknown, partition type 0x82

Error 24: Attempt to access block outside partition


find /boot/grub/stage1
(hd0,4)
(hd0,5)
(hd0,6)



root (fd0,0)

Error 11: Unrecognized device string.


**Do ESCAPE to return to the grub menu and try to select the line I have to boot to that USB Key. I do an EDIT on it to get:**

root (fd0,0)
chainloader +1

**Type B to boot from this but get :**

Error 18: Selected cylinder exceeds maximum supported by BIOS.


**Then I do ESCAPE and no matter which O/S I try to boot from the Grub menu, I get :**

Error 18: Selected cylinder exceeds maximum supported by BIOS.


**The only way out is to Ctrl+Alt+Delete and not select that USB Key grub menu item to be able to boot to any O/S.**


Any questions or suggestions to help me be able to boot to that USB Keyed Kubuntu 8.10 ????

---

### Post by Browser_ice on 2009-10-20
Anyone care to help me figure this out ?

I really need this.

---

### Post by Browser_ice on 2009-10-23
I guess no one knows or its the same problem as usual in these forums, threads go by too fast for anyone to see them.

---

