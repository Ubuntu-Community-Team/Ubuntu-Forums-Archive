---
title: "ext4 problems with 10.10"
date: 2011-04-17
forum: Hardware
---

### Post by jaredheath on 2011-04-17
I'm having loads of problems with 10.10 and new ext4 partitions.  I've tried with Gparted, fdisk, and the Disk Utility and all eventually spool the same issue when trying to mount:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.  

syslog has the following:

ext4_check_descriptors:  Checksum for group 8 failed (43708!=27285) 

and

group descriptors corrupted.

Note I can create ext2 and ext3 partitions with no trouble.  This is happening across multiple devices as well, so the hardware isn't the issue here.

After Gparted makes and ext4 partition, it has a red exclamation point next to it, but I don't see anything in the information tab on the partition that points to an issue.

Size also doesn't appear to be a factor...I've tried 1gb, 100gb, and 500gb partitions and they all come out the same.

running fsck spawns an even more curious error:  fsck.ext4:  Value too large for defined data type while checking ext3 journal for <directory>

Any thoughts on this?

---

