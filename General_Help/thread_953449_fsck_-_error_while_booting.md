---
title: "fsck - error while booting?"
date: 2008-10-20
forum: General Help
---

### Post by metalgearac!d on 2008-10-20
Im a noob. It happens.
Whenever I boot ubuntu studio I get an error on filesystem /dev/sda4 which is my /home partition. This is what the checkfs file says:

Log of fsck -C3 -R -A -a 
Mon Oct 20 07:07:55 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda3: clean, 48/917504 files, 88616/3662820 blocks
/dev/sda4 contains a file system with errors, check forced.
Error reading block 65546 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/dev/sda4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Mon Oct 20 07:08:26 2008
----------------

I dont understand what the issue is, nor do I know what to do. 
Please help.

---

### Post by PocketDog on 2008-10-20
*Don't run fsck on a mounted partition*. To run it manually, reboot to a command line and run fsck from there. If it fails come back here with the error. Also, 'man fsck' in Terminal will shed some light on exactly what it does and doesn't do

---

### Post by ajgreeny on 2008-10-20
Run fsck from a live CD, not from your installed ubuntu.  In live CD terminal check the partitions with ```
sudo fdisk -l
``` and if sda4 is the problem partition then run ```
sudo fsck /dev/sda4
```

---

### Post by metalgearac!d on 2008-10-20
OK...I tried what you suggested (thank you by the way)..but I dont think it really did too much. I tried each of the y/n choices I had at each step but I seem to get the same error. I sort of get the feeling I might have to do a fresh install? or format the partition?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068226

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         304     2441848+  82  Linux swap / Solaris
/dev/sda2   *         305        2128    14651280   83  Linux
/dev/sda3            2129        3952    14651280   83  Linux
/dev/sda4            3953       19457   124543912+  83  Linux
ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda4 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 65546 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (16640): Can't read next inode
e2fsck: aborted
ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda4 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 65546 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 65547 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? no

Error reading block 65548 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (16640): Can't read next inode
e2fsck: aborted

---

### Post by metalgearac!d on 2008-10-21
anyone?

---

