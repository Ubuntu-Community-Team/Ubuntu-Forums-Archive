---
title: "Ext4 Partition doesn't mount, unable to read superblock, zero length partition?"
date: 2012-04-30
forum: Hardware
---

### Post by evanevan on 2012-04-30
We have a hard drive that was set up to dual boot ubuntu and windows. The ubuntu partition spontaneously wouldn't mount as of a few days ago. The other partitions still mount just fine, so I presume this is not a hardware issue with the physical drive (though let me know if i could be wrong). 

Below is some relevant output from some commands I've tried based on some other vaguely-similar threads. Any help is appreciated, as I'm in a bit over my head, and, like many fallible humans, have data on that partition that hasn't been backed up.

Thanks!

```
evan@miquelon:~$ sudo mount -t ext4 /dev/sdc3 /rachel
mount: wrong fs type, bad option, bad superblock on /dev/sdc3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

evan@miquelon:~$ dmesg | tail
[   55.195803] EIP: [<c035de9a>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:e9fd3d6c
[   55.195809] CR2: 0000000000fba000
[   55.195813] ---[ end trace 494244a23c37992f ]---
[   63.540032] wlan0: no IPv6 routers present
[ 1697.805719] attempt to access beyond end of device
[ 1697.805724] sdc3: rw=0, want=4, limit=2
[ 1697.805729] EXT4-fs (sdc3): unable to read superblock
[ 3393.887917] attempt to access beyond end of device
[ 3393.887926] sdc3: rw=0, want=4, limit=2
[ 3393.887932] EXT4-fs (sdc3): unable to read superblock

evan@miquelon:~$ sudo fsck -t ext4 /dev/sdc3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc3
Could this be a zero-length partition?

evan@miquelon:/$ sudo mke2fs -n /dev/sdc3
mke2fs 1.41.11 (14-Mar-2010)
mke2fs: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).
``` 

Thanks again.

---

### Post by ahallubuntu on 2012-04-30
Evan, I would rule out hardware issues by checking the drive's S.M.A.R.T. status with GSmartControl - easy to install if you have another working Linux installation.  Otherwise, you can just grab a Parted Magic CD (a nice little Linux distro with a great set of tools), download and boot it Parted Magic with that drive attached.  Then click on SmartControl.  Look at any Attributes on the Attributes tab that are highlighted in Red. 

Or just open a terminal and do

smartctl -a /dev/sda

and report the output here (assuming /dev/sda if your hard drive of interest).

---

### Post by oldfred on 2012-05-01
Post this as it sounds like partition is bigger than it is supposed to be.

sudo fdisk -lu

---

### Post by evanevan on 2012-05-02
Thanks for the help.

Plugging the drive into a different (Arch Linux) system allowed it to mount. Not sure of the exact problem, but I got the data off and reformatted and installed before getting to try your suggestions. 

Thanks again for offering help!

---

