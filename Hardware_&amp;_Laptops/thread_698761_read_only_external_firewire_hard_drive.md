---
title: "read only external firewire hard drive"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by roofninja on 2008-02-16
I am having problems with my external hard drive. It is a firewire drive and when I turn it on, the PC sees it as read only.  This is a problem for me as ALL of my files are on this drive.  Thanks for any help.

mtab:
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

-------------------------------------------------------------------------
I ran a "dmesg | tail" and this is what I got.

[  790.762350] sd 7:0:0:0: [sdb] Got wrong page
[  790.762352] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  790.762354]  sdb: sdb1
[  790.767448] sd 7:0:0:0: [sdb] Attached SCSI disk
[  790.767470] sd 7:0:0:0: Attached scsi generic sg1 type 0
[  816.979080] FAT: Filesystem panic (dev sdb1)
[  816.979083]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  816.979086]     File system has been set read-only
[  851.053137] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[  851.053143] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0001a39500030316]
-----------------------------------------------------------------------
Here is my "sudo fdisk -l" 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000402ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1946    15631213+  82  Linux swap / Solaris
/dev/sda2   *        1947        1958       96390   83  Linux
/dev/sda3            1959        8037    48829567+  83  Linux
/dev/sda4            8038       22627   117194175   83  Linux

---

