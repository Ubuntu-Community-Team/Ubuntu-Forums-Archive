---
title: "Disk /dev/md0 doesn't contain a valid partition table; No partitions found;"
date: 2017-01-12
forum: Hardware
---

### Post by sn00zy on 2017-01-12
Hello everybody,
After a hard disk error (/dev/sda) in a raid and the exchange of the hard disk I have the following problem:

fdisk says there are no valid partion tables for the Raid:
```

sudo fdisk -l


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55555555


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    50333696    25165824+  fd  Linux raid autodetect
/dev/sdb2        50335744    51384320      524288+  fd  Linux raid autodetect
/dev/sdb3        51386368  3907027120  1927820376+  fd  Linux raid autodetect


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    50333696    25165824+  fd  Linux raid autodetect
/dev/sda2        50335744    51384320      524288+  fd  Linux raid autodetect
/dev/sda3        51386368  3907027120  1927820376+  fd  Linux raid autodetect


Disk /dev/md0: 25.8 GB, 25752895488 bytes
2 heads, 4 sectors/track, 6287328 cylinders, total 50298624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/md1: 536 MB, 536543232 bytes
2 heads, 4 sectors/track, 130992 cylinders, total 1047936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table


Disk /dev/md2: 1974.0 GB, 1973953691648 bytes
2 heads, 4 sectors/track, 481922288 cylinders, total 3855378304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md2 doesn't contain a valid partition table

```

```



sudo sfdisk -d
# partition table of /dev/sdb
unit: sectors


/dev/sdb1 : start=     2048, size= 50331649, Id=fd
/dev/sdb2 : start= 50335744, size=  1048577, Id=fd
/dev/sdb3 : start= 51386368, size=3855640753, Id=fd
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sda
unit: sectors


/dev/sda1 : start=     2048, size= 50331649, Id=fd
/dev/sda2 : start= 50335744, size=  1048577, Id=fd
/dev/sda3 : start= 51386368, size=3855640753, Id=fd
/dev/sda4 : start=        0, size=        0, Id= 0


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md0: unrecognized partition table type
No partitions found


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md1: unrecognized partition table type
No partitions found


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md2: unrecognized partition table type
No partitions found

```

the mdstat looks fine:

```
cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda3[3] sdb3[2]
      1927689152 blocks super 1.2 [2/2] [UU]


md1 : active raid1 sda2[3] sdb2[2]
      523968 blocks super 1.2 [2/2] [UU]


md0 : active raid1 sda1[3] sdb1[2]
      25149312 blocks super 1.2 [2/2] [UU]


unused devices: <none>

```

gdisk says a valid MBR is is on both disks:

```
sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.5


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************


Disk /dev/sdb: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): C0B3D555-2A27-42A0-BCBE-1CBD0B234112
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 8122 sectors (4.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        50333696   24.0 GiB    FD00  Linux RAID
   2        50335744        51384320   512.0 MiB   FD00  Linux RAID
   3        51386368      3907027120   1.8 TiB     FD00  Linux RAID

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.5


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************


Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): DE3E8CDC-1BC4-4464-83D7-34BC3561D8CF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 8122 sectors (4.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        50333696   24.0 GiB    FD00  Linux RAID
   2        50335744        51384320   512.0 MiB   FD00  Linux RAID
   3        51386368      3907027120   1.8 TiB     FD00  Linux RAID

```

Where is the problem here and what do I have to do to solve it?
Thank you!

---

### Post by SeijiSensei on 2017-01-12
The arrays don't have partition tables; they are not physical drives.

What is the exact problem you are trying to solve?  Can you mount /dev/md[012] and use them successfully?

When you replaced the drive, did you see it being rebuilt?

---

### Post by sn00zy on 2017-01-12
I think it is not correct as disk identifier [COLOR=#000000][FONT=&quot]0x00000000 [/FONT][/COLOR]is displayed. On other servers with software raids i don't have this error message:

```

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md1: unrecognized partition table type
No partitions found

```

And the last problem - Why is no boot partition selected?

The server is running and use the partions /dev/md[012] successfully. I removed the sda[123] from the raid and added it again. In the moment a rebuild is running. I'm afraid that if the server shutdown he will not reboot

---

### Post by SeijiSensei on 2017-01-13
Is the /boot partition a RAID device?  I never do that myself.  I only use RAID for locations like /home or /var which have changing content.  Even /usr isn't really worth a RAID array.  And I back up locations like /etc to an external device each night.  Remember the adage, "RAID is not a substitute for backups."

The only time I've had the boot partition on an array is when I'm using a hardware RAID adapter like those SAS devices that come with servers from Dell.  Then the entire array appears as just one device to the OS.

---

