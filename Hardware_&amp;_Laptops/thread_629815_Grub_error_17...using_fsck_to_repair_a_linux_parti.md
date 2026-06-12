---
title: "Grub error 17...using fsck to repair a linux partition"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by phineaus on 2007-12-02
So here goes round number 2!   

I recently rebooted my desktop PC that has been up and running for quite some time without problems, and received error 18 from Grub, resulting in me not being able to boot in either WinXP or UBUNTU Gutsy.  To make a long story short, I did not update or change anything...I was just rebooting because it was slow.  I posted this thread about it and if you would like the long story check it out:

[http://ubuntuforums.org/showthread.php?t=625568](http://ubuntuforums.org/showthread.php?t=625568) 

That entailed me booting the live CD, checking the partition table after installing testdisk, and eventually changing the number of heads from 16 to 255 in order to have it read the partition correctly.  Basically, before or after this change, testdisk could not output the contents of my linux partition, saying that it seemed damaged.  After the change, I get error 17 from Grub.  I think some part of the filesystem is damaged, and I want to learn how to use fsck to try and fix it and recover my data.  Any recommendations on how to do that? 

The following is a printout of my fdisk results and what happens when I try to run fsck on that partition:

ubuntu@ubuntu:~$ sudo fsck -v -f /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo mke2fs -n /dev/hda5
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
5636096 inodes, 11261549 blocks
563077 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
344 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424

ubuntu@ubuntu:~$ sudo fsck -b 32768 -v -f /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo fsck -b 32768 -cf /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783d8f59

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1612 12948358+ 7 HPFS/NTFS
/dev/hda2 1613 7297 45664731 f W95 Ext'd (LBA)
/dev/hda5 1613 7220 45046197 83 Linux
/dev/hda6 7221 7297 618471 82 Linux swap / Solaris

Disk /dev/hdd: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7be346

Device Boot Start End Blocks Id System
/dev/hdd1 * 1 1026 8241313+ 7 HPFS/NTFS
ubuntu@ubuntu:~$

HELP is more than appreciated!  I am an intermediate to basic user...have been only booting UBUNTU for about 9 months now on my laptop and more recently my desktop I got out of storage...

---

