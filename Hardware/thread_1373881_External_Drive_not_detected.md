---
title: "External Drive not detected"
date: 2010-01-06
forum: Hardware
---

### Post by maluka on 2010-01-06
Hi! My machine is unable to read my 500GB external hard drive. It was incorrectly disconnected from another machine running OSX while a file was being transferred. Is there a way for me to repair the disk or at least retrieve my data from there?

lsub results
```

Bus 001 Device 013: ID 059b:0470 Iomega Corp. 
Bus 001 Device 008: ID 056a:00b8 Wacom Co., Ltd 
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04f2:b130 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 0930:020f Toshiba Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


"sudo fdisk -l" results
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf60132be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
/dev/sda2             192       37512   299778048    7  HPFS/NTFS
/dev/sda3           37512       38914    11255808   17  Hidden HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8bfeab9f

Disk /dev/sdb doesn't contain a valid partition table

```

---

### Post by bobcollard on 2010-01-06
> **maluka said:**
> Hi! My machine is unable to read my 500GB external hard drive. It was incorrectly disconnected from another machine running OSX while a file was being transferred. Is there a way for me to repair the disk or at least retrieve my data from there?

lsub results
```

Bus 001 Device 013: ID 059b:0470 Iomega Corp. 
Bus 001 Device 008: ID 056a:00b8 Wacom Co., Ltd 
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04f2:b130 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 0930:020f Toshiba Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```"sudo fdisk -l" results
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf60132be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
/dev/sda2             192       37512   299778048    7  HPFS/NTFS
/dev/sda3           37512       38914    11255808   17  Hidden HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8bfeab9f

Disk /dev/sdb doesn't contain a valid partition table

```
Have you tried hooking it back to the Apple computer?  If nothing else you could use some recovery software on that computer to save what is left.  FAT 32 is readable in OSX and Linux, NTFS if you have the right software on both machines.   Looks like it is NTFS.

---

### Post by maluka on 2010-01-06
Hi Robert. I've tried that already. It was Fat32 formatted. I'm about to try gpart [http://en.wikipedia.org/wiki/Gpart](http://en.wikipedia.org/wiki/Gpart). Fingers crossed ;)

---

### Post by maluka on 2010-01-06
Running TestDisk at the moment. It found the disk and the errors.

---

### Post by bobcollard on 2010-01-06
> **maluka said:**
> Running TestDisk at the moment. It found the disk and the errors.
Looks like this is working for you.  If it fixes this problem be sure to edit your first title to include [Solved] so others can find it and get solutions.

---

### Post by maluka on 2010-01-06
TestDisk worked!:popcorn::guitar:=D>

---

