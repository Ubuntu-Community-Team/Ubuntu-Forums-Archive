---
title: "Unable to mount HDD - group descriptors corrupted"
date: 2009-10-07
forum: Hardware
---

### Post by howcome on 2009-10-07
I just purchased a new Seagate Freeagent 2TB USB HDD. I've used 'fdisk' to set the only partition to type 83. I've used mkfs.ext2 (and mkfs.ext3) to create a file system. So far so good. I've done this before with success on various 1TB disks.

The problem starts when trying to mount the disk. I'm told:

  mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Looking in the syslog I find:

   Oct  7 17:22:43 tuva kernel: [150796.913509] EXT2-fs error (device sdc1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 524288)!
   Oct  7 17:22:43 tuva kernel: [150796.913526] EXT2-fs: group descriptors corrupted!

Running fsck fixes the problem. I can now mount the disk and write to it. However, after unmounting it (cleanly) the same problem occurs. It seems I cannot mount the disk without running fsck first. 

Here is the output from fsck:

root@tuva:~# fsck /dev/sdc1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Group descriptors look bad... trying backup blocks...
/dev/sdc1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #55 (32254, counted=0).
Fix<y>? yes

Free blocks count wrong for group #56 (32254, counted=0).
Fix<y>? yes

Free blocks count wrong for group #57 (32254, counted=0).
Fix<y>? yes

Free blocks count wrong for group #58 (32254, counted=0).
Fix<y>? yes

Free blocks count wrong for group #59 (32254, counted=0).
Fix<y>? yes

Free blocks count wrong for group #60 (32254, counted=14107).
Fix<y>? yes

Free blocks count wrong for group #61 (32254, counted=32246).

etc. etc.

Suggestions welcome.

---

### Post by howcome on 2009-10-08
It seems I found a solution by decreasing the size of the partition slightly.

---

