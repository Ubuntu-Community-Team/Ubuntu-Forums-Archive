---
title: "Mounting External HDD"
date: 2008-05-09
forum: Hardware
---

### Post by killtacular on 2008-05-09
I am having trouble mounting an External HDD in Ubuntu 8.04.  Its formatted in NTFS.  I've tried reading multiple threads, but still am having trouble.

---

### Post by killtacular on 2008-05-09
```
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
```

This is the output of sudo fdisk -l, cat /etc/mta

---

### Post by killtacular on 2008-05-09
output of sudo fdisk -l

```
fdisk: invalid option -- ,

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
phil@phil-desktop:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcda1cda1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9848    79104028+  83  Linux
/dev/sda2            9849       10011     1309297+   5  Extended
/dev/sda5            9849       10011     1309266   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

```

---

### Post by killtacular on 2008-05-09
The newest output.

```
total 0
drwxr-xr-x 2 root root 240 2008-05-09 00:36 .
drwxr-xr-x 6 root root 120 2008-05-09 00:36 ..
lrwxrwxrwx 1 root root   9 2008-05-08 23:43 ata-HDS722580VLAT20_VNR81EC2D0GR0L -> ../../sda
lrwxrwxrwx 1 root root  10 2008-05-08 23:43 ata-HDS722580VLAT20_VNR81EC2D0GR0L-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-05-08 23:43 ata-HDS722580VLAT20_VNR81EC2D0GR0L-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-05-08 23:43 ata-HDS722580VLAT20_VNR81EC2D0GR0L-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-05-08 23:43 scsi-1ATA_HDS722580VLAT20_VNR81EC2D0GR0L -> ../../sda
lrwxrwxrwx 1 root root  10 2008-05-08 23:43 scsi-1ATA_HDS722580VLAT20_VNR81EC2D0GR0L-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-05-08 23:43 scsi-1ATA_HDS722580VLAT20_VNR81EC2D0GR0L-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-05-08 23:43 scsi-1ATA_HDS722580VLAT20_VNR81EC2D0GR0L-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-05-09 00:36 usb-WDC_WD800BB-00DKA0_AA040115020086-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-05-09 00:36 usb-WDC_WD800BB-00DKA0_AA040115020086-0:0-part1 -> ../../sdb1
```

---

### Post by HangukMiguk on 2008-05-09
> **killtacular said:**
> output of sudo fdisk -l

```
fdisk: invalid option -- ,

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
phil@phil-desktop:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcda1cda1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9848    79104028+  83  Linux
/dev/sda2            9849       10011     1309297+   5  Extended
/dev/sda5            9849       10011     1309266   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

```

In terminal: 
sudo gedit /etc/fstab

append the following line at the bottom:

/dev/sdb1        /media/external   ntfs user,noauto 0       0

Save & close.

sudo mkdir /media/external
mount /media/external

---

