---
title: "Error fsyncing/closing /dev/sdb: Input/output error"
date: 2017-04-22
forum: Hardware
---

### Post by ADO_kg on 2017-04-22
Hi,

i have an Asus UX32a, it came with 320GB HDD, and besides it has built-in disk for ExpressCache  - Sandisk SSD i100 24GB.
as Laptop came with installed Windows, 24GB was used for ExpressCache. Two years ago I  replaced HDD with  SSD 256GB, and Installed Windows 10 directly on this disk. Installed Ubuntu 14 on 24GB built-in disk, but that time could not make dual boot and was using Windows 10 only. So, 24GB disk was not in use around 2 years. 
Few days ago i wanted to install Ubuntu, but could not install on 24GB, and made a fresh install on 256GB disk, replaced Windows.

after i could not make dual boot (Windows on 256GB and Ubuntu on 24GB), Windows was not seeing the 24GB disk. Before that I remember i was using that inbuit disk for some VMs.

I would like to get this disk back alive and use it, would like to install Ubuntu on 24GB disk, pls guide me.

here are the some data:

**$ sudo parted -l**
Model: ATA TS256GSSD370 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   256GB  256GB  extended
 5      513MB   256GB  256GB  logical


Warning: Error fsyncing/closing /dev/sdb1: Input/output error
Retry/Ignore? i                                                           
Warning: Error fsyncing/closing /dev/sdb: Input/output error
Retry/Ignore? i                                                           
Model: ATA SanDisk SSD i100 (scsi)
Disk /dev/sdb: 24,0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  24,0GB  24,0GB  ntfs         Basic data partition  msftdata


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 6320MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  6320MB  6320MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 6321MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  6321MB  6321MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 249GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0,00B  249GB  249GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/sda5_crypt: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: Linux File-CD Gadget (scsi)                                        
Disk /dev/sr0: 6089kB
Sector size (logical/physical): 512B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name                             Flags
 1      512B    18,4kB  17,9kB               MRKS
 2      55,3kB  6089kB  6033kB  hfs+         Toast 11.0.0 HFS+/Joliet Builde


**$ sudo fdisk -lu**
Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcb2a3748

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sda1  *       2048    999423    997376  487M 83 Linux
/dev/sda2       1001470 500117503 499116034  238G  5 Extended
/dev/sda5       1001472 500117503 499116032  238G 83 Linux


Disk /dev/sdb: 22,4 GiB, 24015495168 bytes, 46905264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FB26DFA8-A671-4119-B025-8E50F918B275

Device     Start      End  Sectors  Size Type
/dev/sdb1   2048 46903295 46901248 22,4G Microsoft basic data


Disk /dev/mapper/sda5_crypt: 238 GiB, 255545311232 bytes, 499111936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 232,1 GiB, 249175212032 bytes, 486670336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 5,9 GiB, 6320816128 bytes, 12345344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1: 5,9 GiB, 6320291840 bytes, 12344320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**$ sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1**
1+0 records in
1+0 records out
512 bytes copied, 0,0704172 s, 7,3 kB/s

---

