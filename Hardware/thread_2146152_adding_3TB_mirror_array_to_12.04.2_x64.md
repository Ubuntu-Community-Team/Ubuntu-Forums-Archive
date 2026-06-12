---
title: "adding 3TB mirror array to 12.04.2 x64"
date: 2013-05-17
forum: Hardware
---

### Post by w_boba on 2013-05-17
I have 1TB SATA boot/OS drive on Intel motherboard. I would like to add 2x 3TB drives in mirror to it for storage. For some reason I see only 802GB volume available. Is there any way to format this mirror volume to 3TB single partition ? I do not have any issues to partition each individual drive, but when I create mirror using built into MB RAID management, I can only see 802GB volume.

```
MB: 
Base Board Information
        Manufacturer: Intel Corporation
        Product Name: DZ75ML-45K
        Version: AAG75008-102

#parted > print all

GNU Parted 2.3
Using /dev/mapper/isw_cabbidfgbd_Volume0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p all
Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/isw_cabbidfgbd_Volume0: 802GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End  Size  File system  Flags


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End  Size  File system  Flags


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End  Size  File system  Flags


Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  992GB   992GB   primary   ext4            boot
 2      992GB   1000GB  8414MB  extended
 5      992GB   1000GB  8414MB  logical   linux-swap(v1)
```

---

