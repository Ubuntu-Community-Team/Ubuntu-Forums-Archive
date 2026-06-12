---
title: "No longer booting:  BIOSDISK READ ERROR"
date: 2010-03-24
forum: Hardware
---

### Post by ryanshaw on 2010-03-24
I have something that seems like hard drive problems but I want to confirm it before I purchase and replace.  I’m fairly new to Ubuntu and just loaded 9.10 to my Acer Aspire One (AOA110)

It worked for about a month and then started to not boot.  I ran from live USB and ran fsck a couple times and got different results but fixed.  It booted a few more times and then started with the grub:

BIOSDISK READ ERROR.

I’ve tried three different things (below) from live USB but no change.   I am able to mount the drive in live mode and browse all files (all from what I can tell)

Any suggestions?

------

ubuntu@ubuntu:~$ sudo fsck -pcfc /dev/sda1
fsck from util-linux-ng 2.16
badblocks: Input/output error during test data write, block 230848
/dev/sda1: Updating bad block inode.
Error reading block 491 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

-------

ubuntu@ubuntu:~$ sudo fsck -f -y /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 170468/468640 files (0.2% non-contiguous), 967009/1871564 blocks
ubuntu@ubuntu:~$ 


------

TestDisk did not find anything wrong either.

-------

---

