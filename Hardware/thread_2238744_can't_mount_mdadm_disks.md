---
title: "can't mount mdadm disks"
date: 2014-08-09
forum: Hardware
---

### Post by reggler on 2014-08-09
hi,

i used a RAID 1 array with two disks containg two partitions but since I updated to 14.04, my partuitions would n't mount anymore. I've tried all kinds of things, by now I just totally disabled my raid array, trying to gain access to my data. 
My disk layout looks like:
```
reg@regDesktopHome:~$ sudo lshw -class disk
[sudo] password for reg: 
  *-disk:0                
       description: ATA Disk
       product: TOSHIBA MK7559GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: GN00
       serial: Y1OCC5HLT
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=17f9300d
  *-disk:1
       description: ATA Disk
       product: ST31000528AS
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: CC34
       serial: 6VP0308B
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=000133c6
  *-cdrom
       description: DVD-RAM writer
       product: DVD A  DH24ABS
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: AAA1
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: ST31000528AS
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/sdc
       version: CC34
       serial: 5VP0DG2K
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=000133c6
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdd
       configuration: sectorsize=512
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sde
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@5:0.0.1
       logical name: /dev/sdf
       configuration: sectorsize=512
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@5:0.0.2
       logical name: /dev/sdg
       configuration: sectorsize=512
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@5:0.0.3
       logical name: /dev/sdh
       configuration: sectorsize=512
reg@regDesktopHome:~$
```
So when I try to mount my ex raid parition, I just get:
```
reg@regDesktopHome:~$ sudo mount /dev/sdb6 /mnt/sdb6
mount: /dev/sdb6 is not a block device
```
but with gparted, i can see that my disk **/dev/sdb** has a partition **/dev/sdb6** - what's going on here? Let's see...:

Also, **fdisk -l** lists:
```

reg@regDesktopHome:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x17f9300d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29747199    14872576   1b  Hidden W95 FAT32
/dev/sda2   *    29747200   127403449    48828125    7  HPFS/NTFS/exFAT
/dev/sda3       127404030  1465147391   668871681    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       776648704  1122993085   173172191   83  Linux
/dev/sda6      1448411136  1465147391     8368128   82  Linux swap / Solaris
/dev/sda7       127404032   562378197   217487083   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000133c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   195318269    97659103+  83  Linux
/dev/sdb2       976575285  1953503999   488464357+   5  Extended
/dev/sdb3       195318270   976575284   390628507+  83  Linux
/dev/sdb5      1941535638  1953503999     5984181   82  Linux swap / Solaris
/dev/sdb6       976575411  1464854894   244139742   83  Linux
/dev/sdb7      1464854958  1941535574   238340308+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000133c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   195318269    97659103+  83  Linux
/dev/sdc2       976575285  1953503999   488464357+   5  Extended
/dev/sdc3       195318270   976575284   390628507+  83  Linux
/dev/sdc5      1941535638  1953503999     5984181   82  Linux swap / Solaris
/dev/sdc6       976575411  1464854894   244139742   83  Linux
/dev/sdc7      1464854958  1941535574   238340308+  83  Linux

Partition table entries are not in disk order

Disk /dev/mapper/isw_cabciecjfi_Raid: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000133c6

                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cabciecjfi_Raid1   *          63   195318269    97659103+  83  Linux
/dev/mapper/isw_cabciecjfi_Raid2       976575285  1953503999   488464357+   5  Extended
/dev/mapper/isw_cabciecjfi_Raid3       195318270   976575284   390628507+  83  Linux
/dev/mapper/isw_cabciecjfi_Raid5      1941535638  1953503999     5984181   82  Linux swap / Solaris
/dev/mapper/isw_cabciecjfi_Raid6       976575411  1464854894   244139742   83  Linux
/dev/mapper/isw_cabciecjfi_Raid7      1464854958  1941535574   238340308+  83  Linux

Partition table entries are not in disk order

Disk /dev/mapper/isw_cabciecjfi_Raid1: 100.0 GB, 100002921984 bytes
255 heads, 63 sectors/track, 12157 cylinders, total 195318207 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cabciecjfi_Raid1 doesn't contain a valid partition table
fdisk: unable to read /dev/mapper/isw_cabciecjfi_Raid2: Inappropriate ioctl for device
reg@regDesktopHome:~$ 
```

I assume the **/dev/mapper/isw_cabciecjfi_Raid** device is some kind of fake raid from the BIOS and added supper for it in **14.04** might have broken my previos **mdadm **
Then I tried:
```

reg@regDesktopHome:~$ sudo mount /dev/mapper/isw_cabciecjfi_Raid6 /mnt/sdb6
mount: unknown filesystem type 'linux_raid_member'

```
GREAT!!! How further?
Thank you,
Ron

---

