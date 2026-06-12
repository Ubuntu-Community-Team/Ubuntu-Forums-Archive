---
title: "drive space problem"
date: 2009-05-29
forum: Hardware
---

### Post by phh on 2009-05-29
My desktop has a 80gb Maxtor hard drive. After several distro install/uninstalls the drive size is suddenly 20.5gb ??? GParted also only reports 20.5gb as does Seatools from Seagate. I suppose I might have messed up the partitions somewhere... Anyone have any ideas?

---

### Post by x33a on 2009-05-29
post the output of
```
sudo fdisk -l
df -h
```

---

### Post by phh on 2009-05-29
> **x33a said:**
> post the output of
```
sudo fdisk -l
df -h
```
Output as requested (terminal from live CD - Ubuntu not installed to drive)

**fdisk -h**
Disk /dev/sda: 20.5GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a(af8

**df -h**
File  System Size  Used  Available  Use%  Mounted on
tmpfs    497M      2.4M    495M      1%   /lib/modules/2.6.28-11-generic/volat
ile
tmpfs    497M      2.4M    495M      1%   /lib/modules/2.6.28-11-generic/volat
ile
tmpfs    497M       0      497M      0%   /lib/init/rw
varrun   497M       96K    497M      1%   /var/run
varlock  497M       0      497M      1%   /var/lock
udev     497M      128K    497M      1%   /dev
tmpfs    497M       76K    497M      1%   /dev/shm
rootfs   497M       17M    480M      4%   /
/dev/sr0 699M      699M      0      100%  /cdrom
/dev/loop0 676M    676M      0      100%  /rofs
tmpfs     497M      12K    497M      1%   /tmp

---

### Post by x33a on 2009-05-29
hi, the output of **fdisk -l** is missing.

df -h, won't be much useful from a live cd.

---

### Post by phh on 2009-05-30
> **x33a said:**
> hi, the output of **fdisk -l** is missing.

df -h, won't be much useful from a live cd.
Hi x33a

Sorry, my mistake... First output report is from fdisk -l

I will install 9.04 and report df -h...as soon as I can get to the machine again.

Many thanks

---

### Post by x33a on 2009-05-30
the output of fdisk -l isn't complete.

anyway, post the output of both these commands, when you finish the installation.

---

### Post by phh on 2009-06-09
> **x33a said:**
> the output of fdisk -l isn't complete.

anyway, post the output of both these commands, when you finish the installation.
Output from 9.04 install to 20.5Gb(80Gb) disk:

**fdisk -l**

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2388    19181578+  83  Linux
/dev/sda2            2389        2498      883575    5  Extended
/dev/sda5            2389        2498      883543+  82  Linux swap / Solaris

**df -h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.1G   16G  12% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  104K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  140K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile

Hope we can get some light on this problem?

---

### Post by x33a on 2009-06-11
sorry for the late reply.

well your problem is really strange, since fdisk and df also show the space as 20 GB.

run fsck and see if reports some errors.

if it doesn't work, try seatools or maxtor specific software (if available) diagnostics.

if your drive is under warranty, send it for replacement, but before that try contacting  maxtor support.

---

