---
title: "The superblock could not be read or does not describe a correct ext2 filesystem"
date: 2010-07-29
forum: Hardware
---

### Post by s0l1dsnak3123 on 2010-07-29
Hey there. I have a tmobile pulse android phone which I'm trying to connect via USB to, to access its partition. When I attempt to access the partition, I get the following:
> Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
So I checked out dmesg | tail and got this:
> [30193.160800]  sdc: sdc1 sdc2
[30194.492731] VFS: Can't find ext3 filesystem on dev sdc1.
[30194.632723] VFS: Can't find ext3 filesystem on dev sdc1.
[30195.294621] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[30214.116983] VFS: Can't find ext3 filesystem on dev sdc1.
[30214.221963] VFS: Can't find ext3 filesystem on dev sdc1.
[30336.429813] VFS: Can't find ext3 filesystem on dev sdc1.
[30350.525841] VFS: Can't find ext3 filesystem on dev sdc1.
[30352.633542] VFS: Can't find ext3 filesystem on dev sdc1.
[30375.393474] VFS: Can't find ext3 filesystem on dev sdc1.

(the partition I'm trying to access is called /dev/sdc1).

So I followed the advice and ran e2fsck, and got the following:
> e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;



(yes - including the "&gt;" part - not a greater than symbol). So I did as was told and tried that command:

> john@panther:~$ sudo e2fsck -b 8193 /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;


 And I got the same error. Can anyone shine a light onto this problem?

---

### Post by vincenma on 2010-09-24
Hi,

I had the same problem and after many tries at googling a solution, I finally found this link explaining how to use TestDisk to fix the 'superblock could not be read' problem.

[http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock]("http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock")

You can find the TestDisk soft on the same site or in the depots (ie : via synaptic or apt-get). 

It worked great for me, saved my data!! :)


btw : TestDisk is OpenSource software and is licensed under the terms of the GNU General Public License (GPL). I have no affiliations whatsoever with the author; its just great OSS software and I hope it can help someone else :)

---

