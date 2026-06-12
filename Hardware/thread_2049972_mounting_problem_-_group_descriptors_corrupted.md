---
title: "mounting problem - group descriptors corrupted"
date: 2012-08-29
forum: Hardware
---

### Post by benuix on 2012-08-29
Hi there,

I have a problem when trying to mount a Truecrypt volume. 
When I ran the mounting command(of Truecrypt) it returns:
mount: wrong fs type, bad option, bad superblock on /dev/mapper/truecrypt2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and dmesg:
[ 3870.885825] EXT3-fs error (device dm-0): ext3_check_descriptors: Block bitmap for group 1152 not in group (block 2701169)!
[ 3870.885982] EXT3-fs (dm-0): error: group descriptors corrupted

I have tried to run 'fsck /dev/sdb' which gives:
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

and e2fsck does not work with any block number.

Could you help me with that? I have some important stuff in the disk :(!

---

### Post by benuix on 2012-09-03
please :)?

---

### Post by benuix on 2012-09-21
does anyone know?

---

### Post by einonm on 2012-09-21
Hi,

I think you are going along the correct path in trying to do an fsck on the disk, but I believe the parameters are wrong. The drive that the information is on looks to be an LVM volume, and you are trying to check a filesystem on the actual physical disk.

From dmesg, it looks like the device you need to check is actually /dev/dm-0 or similar. If you post the output to 'ls /dev' I may be able to confirm this.

Also, if the data was not on an LVM but a physical disk, you'd need to fsck something like /dev/sda1, which is the filesystem mount point, not /dev/sda, which is the physical disk device mount point.

---

