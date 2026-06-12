---
title: "Partition problem during installation"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by chjustc on 2008-12-14
I tried to install Kubuntu 8.10 for 64-bit machines on my desktop, which has windows Vista as the only operating system.

The installation disk was loaded OK. When the installation came to the part of partitioning hard disk, no windows partition can be found. The installation found /dev/sda and /dev/sdb. But, there was no partition table on either of them. All the space was free.

Then, I opened a shell prompt, and ran
```
ubuntu@ubuntu:~$ sudo fdisk -l
```
I got the results as follows,
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76534   614759323+   7  HPFS/NTFS
/dev/sda2           76535       77826    10377990    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38fb89b5

Disk /dev/sdb doesn't contain a valid partition table
```
Then, I use testdisk to analyze /dev/sda, and got the following,
```
The harddisk (320 GB / 298 GiB) seems too small! (< 629 GB / 586 GiB)
Check the harddisk size: HD jummpers settings, BIOS detections

The following partitions can't be recovered:
Partition          Start         End        Size in sectors
HPFS-NTFS     0    1    1    76533  25463   1229518647
HPFS-NTFS   3917  133  57    75908  22848   1124411392
```
When I chose to deeper search /dev/sda, I got one more partion as follows,
```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914  255 63
   Partition         Start          End      Size in sectors
* FAT32 LBA   29574    0    134243  254  63  75023550 [FREEDOS]
```
When I listed the files in this partition, I saw file names in non-English characters, which I don't recognize at all.

I also analyzed and deeper analyzed /dev/sdb, and got the following,
```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
   Partition         Start          End      Size in sectors

Partition sector doesn't have the end mark OxAA55
```
Is /dev/sda too small? Or, it is caused by some problem with /dev/sdb? How do I fix it?

By the way, By the way, this machine is a new desktop that I bought from HP several months ago. It has windows Vista on it. I have not done anything about partitioning on it after I bought it.

I installed ubuntu several times on my own laptop and other desktops without any problem. I was always able to find the existing (windows) partition. I always left the windows partition alone or just cut the size of it from the end. But, this time, I don't know what is going on. I don't want to break anything on the windows partition.

Thanks.

---

