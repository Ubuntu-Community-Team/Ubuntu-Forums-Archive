---
title: "Use of different file systems in an external hard drive"
date: 2014-12-16
forum: Hardware
---

### Post by %(gej%) on 2014-12-16
Is it possibe to partition an external hard drive with different file systems? For example:
Partition 1 - NTFS
Partition 2 - ext4
Partition 3 - Btrfs
Partition 4 - NTFS

If so can it be used in a Windows PC?

---

### Post by SuperFreak on 2014-12-16
Yes. I have an NTFS external HD that I use for Ubuntu. You can't install home or root on NTFS

---

### Post by sudodus on 2014-12-16
How do you intend to connect the drive? Via USB or eSATA?

eSATA gives you the same options as a normal internal SATA connection. Windows XP could only see the first partition in a USB drive. I tested right now, and it is the same problem in the current Window Technical Preview alias Windows 10. I made two partitions with FAT32 file systems in a USB pendrive. Windows 10 recognizes only the first partition. Maybe there is a way around it, but I don't know how to do it.

***So you need to use the first partition for communication with Windows***. It can be formatted with FAT32 or NTFS, but not with a linux file system.

---

### Post by sudodus on 2014-12-16
> **SuperFreak said:**
> Yes. I have an NTFS external HD that I use for Ubuntu. You can't install home or root on NTFS

+1

Ubuntu needs a linux file system for the root (and home) partitions. Otherwise there will be problems with the permissions. But it can be a good idea to have a ***data*** partition with the NTFS file system, to use from Ubuntu as well as from Windows.

---

### Post by %(gej%) on 2014-12-16
> **sudodus said:**
> How do you intend to connect the drive? Via USB or eSATA?

USB

> **sudodus said:**
> So you need to use the first partition for communication with Windows. It can be formatted with FAT32 or NTFS, but not with a linux file system.

If I do so can I access only the 1st partition or both NTFS partitions (in Windows) in the above example? I know there are some tools to access linux partitions in Windows.

---

### Post by sudodus on 2014-12-16
According to my experience, Windows can access only the first partition in a USB drive. This is independent of the file system.

Yes, there are tools to access ext partitions in Windows, but I have seen some reports that it is not quite reliable, and other reports that it works well.

[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

---

### Post by %(gej%) on 2014-12-16
Thanks everyone...     :D

---

