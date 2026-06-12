---
title: "Question  USB HDD wont show in fdisk -l to mount"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by vikrant_me on 2006-11-20
My External USB HDD having a ntfs file system wont show in fdisk -l (i am looking to mount it) ....What do i do?

---

### Post by xyz on 2006-11-20
Hi - check this out:
[External USB Hard Drive fails to mount!?]("http://ubuntuforums.org/showthread.php?t=48126")
Hope you can work it out. Good luck and welcome.

---

### Post by vikrant_me on 2006-11-20
WEll my device dows not show in fdisk -l or in fstab so how do i go about mounting it? I have seen the post you have givin me the link for but it does not help me identify my hdd

---

### Post by xyz on 2006-11-20
Can you please post the output of:
```
sudo fdisk -l
```
with the external drive plugged in.
Also, while we're at it, the output of:
```
sudo gedit /etc/fstab
```
just to have a look at it.
Thx.

---

### Post by vikrant_me on 2006-11-20
vicky@vicky-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2        9729    78140160    5  Extended
/dev/sda5               2        2612    20972826    7  HPFS/NTFS
/dev/sda6            2613        5223    20972826    7  HPFS/NTFS
/dev/sda7            7837        9729    15205491    7  HPFS/NTFS
/dev/sda8            5224        7518    18434556   83  Linux
/dev/sda9            7519        7836     2554303+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sdb2            2678        9728    56637157+   f  W95 Ext'd (LBA)
/dev/sdb5            2678        9728    56637126    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3189    25615611    7  HPFS/NTFS
/dev/sdc2            3190        9729    52532550    f  W95 Ext'd (LBA)
/dev/sdc5            3190        9729    52532518+   7  HPFS/NTFS
vicky@vicky-desktop:~$


and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda5 /media/sda5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda7 /media/sda7 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
sudo ntfs-3g /dev/sdb1 /media/sdb1 -o umask=0,nls=utf8
#Added by diskmounter utility
/dev/sdb5 /media/sdb5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdc1 /media/sdc1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdc5 /media/sdc5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdd1 /media/sdd1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdd5 /media/sdd5 ntfs ro,user,fmask=0111,dmask=0000 0 0

---

### Post by xyz on 2006-11-20
Try and create (mkdir) for your drive:
```
sudo mkdir /dev/sdc1 
```
and then, mount (make it accessible):
```
mount /media/sdc1
```

Also see this very informative about fstab:
[ by bodhi.zazen]("http://ubuntuforums.org/showthread.php?p=1653968#post1653968")

---

### Post by vikrant_me on 2006-11-20
vicky@vicky-desktop:~$ mount /media/sdc1
[mntent]: line 15 in /etc/fstab is bad
mount: /dev/sdc1 already mounted or /media/sdc1 busy
mount: according to mtab, /dev/sdc1 is already mounted on /media/sdc1

---

### Post by vikrant_me on 2006-11-20
I just think that the hdd is not being detected by either fdisk -l or shown in the fstab

---

### Post by xyz on 2006-11-20
OOps sorry I think I omitted just one major little word in this command line:```
sudo mkdir /dev/sdc1
```
It should read:
```
sudo mkdir /media/sdc1
```
and then:
```
mount /media/sdc1
```
try it ...

---

### Post by vikrant_me on 2006-11-20
vicky@vicky-desktop:~$ sudo mkdir /media/sdc1
Password:
mkdir: cannot create directory `/media/sdc1': File exists

well as you can see in my fstab the partitions from my 3 SATAs are mounted in thir respective folders, just the usb hdd wont show now i need to know the mount -t ntfs /dev/??? /media/usbdrive 

I need to know the ??? and im set

---

### Post by pandu.rs on 2006-11-20
ok..lets find it out!

Make sure that the usb hdd is not connected and run the following command
ls /dev/ > /tmp/before

Plug in the usb hdd and then run
ls /dev/ > /tmp/after

Then see the difference between these two files

vimdiff /tmp/before /tmp/after

so whatever is there in /tmp/after but not in /tmp/before is ur hdd node created!

attach both files (/tmp/before and /tmp/after) in case u still cant solve it.

---

