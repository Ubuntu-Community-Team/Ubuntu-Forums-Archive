---
title: "Unable to mount NTFS external hard disk"
date: 2011-10-15
forum: Hardware
---

### Post by stormdt on 2011-10-15
who can help me??

I have problem when mount external hard disk (it can run on windows).
This is a message error:
> Error mounting: mount exited with exit code 12: Failed to read last sector (312581744): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Some result when i run code
```
sudo mount -t ntfs-3g /dev/sdc1 /media/seconddisk -o force
```

Failed to read last sector (312581744): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

and here
```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=dea3e778-c695-460b-ada6-bec6254d58f7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8eade153-b7df-4f47-8ef4-65f3c3324074 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b0ddec13-f8e9-448f-986d-3ad66b5127be none            swap    sw              0       0

and here
```
 sudo fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4af1646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    94373887    47083520    7  HPFS/NTFS/exFAT
/dev/sda3        94373888   188299263    46962688    7  HPFS/NTFS/exFAT
/dev/sda4       188301310   234440703    23069697    5  Extended
/dev/sda5       230440960   234440703     1999872   82  Linux swap / Solaris
/dev/sda6   *   188301312   208300031     9999360   83  Linux
/dev/sda7       208302080   230434815    11066368   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1995 MB, 1995440128 bytes
39 heads, 38 sectors/track, 2629 cylinders, total 3897344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         131     3897343     1948606+   6  FAT16

Disk /dev/sdc: 160.0 GB, 160041883648 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581804 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00197cae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312581807   156290872+   7  HPFS/NTFS/exFAT

```
ls -l /media
```
total 36
drwxr-xr-x 2 root    root     4096 2011-10-15 07:54 seconddisk
drwx------ 9 stormdt stormdt 16384 1970-01-01 07:00 TRANSCENDSD

---

### Post by stormdt on 2011-10-15
i found the tip to fix this error

```
sudo ntfsfix /dev/sdc1
```

PS: please close this topic, thanks for read

---

