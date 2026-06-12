---
title: "Gparted can't part..."
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Brian Korsedal on 2009-03-01
I'm installing Ubuntu 9.04 Alpha 5 x64 on my Dell Vostro 1500 laptop.  

I'm gparted on the LiveCD.  I'm trying to format my entire hard drive as EXT4.  I have 3 GB of memory and don't want a swap partition.

Every time I try to partition the drive I get an error.  I get the same errors using Ubuntu 8.10, 9.04 alpha 3 and 4.  I also get the same errors if I try to partition to ext3.  

Any suggestions?

Here is the details from Gparted:

GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ext4, 149.05 GiB) on /dev/sda  00:01:21    ( ERROR )
     	
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 312576704
size: 312576642 (149.05 GiB)
set partition type on /dev/sda1  00:00:10    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:01:00    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "" /dev/sda1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
9773056 inodes, 39072080 blocks
1953604 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1193 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done
mke2fs 1.41.4 (27-Jan-2009)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

========================================

---

### Post by roshanjose on 2009-03-01
If you are running on a live cd then, gparted wont work, because there is no allocation to memory

---

### Post by roshanjose on 2009-03-01
If you want to make partitions then first install....then you can use gparted

---

### Post by whoop on 2009-03-01
You can partition your hard disk from a livecd running gparted, that's not the problem.
The problem is ext4. It is probably not working (yet) on the version of gparted (you are using).

try ext3 then convert to ext4 or just make some unpartitioned space and let the jaunty installer use that for it's installation and select ext4 as filesystem.

---

### Post by Brian Korsedal on 2009-03-01
Neither of those work.

The partitioning also crashes during installation.

It crashes with ext3 and ext4.

I think it might be something specific with my make and model.  I have a desktop which ubuntu installs fine on. 

Can anyone look at the log and give me a hint?

---

### Post by Brian Korsedal on 2009-03-02
Is there any way to get an install log?  Turn verbose errors on?  

What should the default partitions be?

---

### Post by Pumalite on 2009-03-02
Have you tried Gparted Live CD?:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. (it works on unmounted drives/partitions)
Good luck.

---

### Post by Brian Korsedal on 2009-03-02
I just downloaded the newest live CD from gparted.  I tried it using ext3.  I got the same error.  

Windows installs fine on this drive.

---

### Post by Pumalite on 2009-03-02
Check your drive with TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
If you can boot a Live CD; post:
sudo fdisk -lu

---

