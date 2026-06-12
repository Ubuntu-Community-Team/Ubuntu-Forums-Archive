---
title: "Cannot create file system on HDD"
date: 2010-08-06
forum: Hardware
---

### Post by FA5878 on 2010-08-06
My desktop has 3 internal HDD's, 2 300GB drives (ATA ST3320620AS) and a 230GB drive (ATA Hitachi HDP72502).

The operating system is set up on one of the 300GB (/dev/sdc) drives and the 230GB HDD has an ext4 file system on it (/dev/sdb).

I originally set up the partitions through terminal, but have since installed and tried GParted which gives me the same problem.

The problem:

I format the drive and try to install a file system (usually ext4) and I get this:
```
GParted 0.5.1

Libparted 2.2

Create Primary Partition #1 (ext4, 298.09 GiB) on /dev/sda  00:00:01    ( ERROR )
    	
create empty partition  00:00:01    ( SUCCESS )
    	
path: /dev/sda1
start: 63
end: 625137344
size: 625137282 (298.09 GiB)
set partition type on /dev/sda1  00:00:00    ( SUCCESS )
    	
new partition type: ext4
create new ext4 file system  00:00:00    ( ERROR )
    	
mkfs.ext4 -j -O extent -L "" /dev/sda1
    	
mke2fs 1.41.11 (14-Mar-2010)
/dev/sda1 is apparently in use by the system; will not make a filesystem here
```

Will appreciate any help you can offer thanks

---

