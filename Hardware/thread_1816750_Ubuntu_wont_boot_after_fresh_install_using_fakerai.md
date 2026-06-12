---
title: "Ubuntu wont boot after fresh install using fakeraid."
date: 2011-08-02
forum: Hardware
---

### Post by Alex1331 on 2011-08-02
Hi!

I am not able to boot Ubuntu server after installation.:(

Error message:
> ALERT! /dev/disk/by-uuid/ac794397-7ebc-4e25-92a3-a2dada60ce01 does not exist. Dropping to a shell!Output of sudo fdisk -l:
> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243200  1953497087+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243200  1953497087+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/dm-0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/dm-0: 2000.4 GB, 2000381018112 bytes
255 heads, 63 sectors/track, 243199 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      243200  1953497087+  ee  GPT

Disk /dev/sdc: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000256a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1015     1006849    c  W95 FAT32 (LBA)I did get it working without any problems in October 2010 with 2x1TB disks in RAID 1, now I am trying to upgrade to 2x2TB disks in RAID 1.(fakeraid)

During the installation I answered yes to a question about SATA RAID.

Do anyone know how to fix this?

---

### Post by psusi on 2011-08-02
GPT is not supported on fakeraid.  Unless you need to dual boot with Windows, don't use fakeraid.  Traditional software raid is much better supported.

---

### Post by Alex1331 on 2011-08-02
Aha! Since the drives are 2 TB it uses GPT, that is why I did not have this problem when using 1 TB drives, right? :)

Thanks, I really appreciate your help. :KS

I will try to set up a software raid now. :)

---

### Post by srs5694 on 2011-08-02
I agree with psusi's comments, and I advise using GPT on Linux-only installations; however, I'd also like to point out that MBR is adequate for disks of up to 2 TiB, which is larger than the 2 TB disks that are available today. (TB = 10^12 bytes, TiB = 2^40 bytes = 1.1 x 10 ^12 bytes, so 2 TiB > 2 TB.) For reasons I don't claim to know, the Ubuntu installer seems to switch from MBR to GPT as the default partitioning system somewhere between 1 TB and 2 TB; but if you want to use MBR, you can do so. You must create your MBR partitions, or at least set up the disk with an empty MBR table, prior to installing Ubuntu. It will then use MBR partitions.

---

### Post by Alex1331 on 2011-08-02
Noob question: Can somebody tell me how to create a software raid? I have tried 4 tutorials now, without success.[-o<

Every time I tried I had a problem installing GRUB.:sad:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Same  problem occurred when following that tutorial. I did also get more than  tow partitions then using "automatically partition the free space".

I wish there was a really easy way of doing this.

---

### Post by psusi on 2011-08-02
> **Alex1331 said:**
> Noob question: Can somebody tell me how to create a software raid? I have tried 4 tutorials now, without success.[-o<

Every time I tried I had a problem installing GRUB.:sad:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Same  problem occurred when following that tutorial. I did also get more than  tow partitions then using "automatically partition the free space".

I wish there was a really easy way of doing this.

If you are using GPT, then you need to create a 1mb bios_grub partition.

---

### Post by Alex1331 on 2011-08-03
I made a 1 MB partition on both drives, and...it is working! :D
Finally! :D

Thank you!

---

