---
title: "Superblock problem"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by Marinodimare on 2008-01-21
HI,

My laptop's HD crashed severely yesterday - it won't do a thing. I've tried cleaning it with a live CD, even tried the gparted livecd, but that one doesn't recognize two of the three partitions (both ext3). The only one it does recognize is swap.

Now, using the ubuntu livecd and ddrescue, I've made a dump of the home partition on my external (ext3, just reformatted) HD. Then, I tried to mount it on my desktop (also ubuntu), and got this error:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The suggested command came up with this:

```
[ 1424.704000] EXT3-fs: sdf1: couldn't mount because of unsupported optional features (1000100).
```

Then, I tried fsck. Output:
```

fsck.ext3: Filesystem revision too high while trying to open /dev/sdf1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Finally, I tried the suggested e2fsck -b 8193. This was the result:
```

e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Bad magic number in super-block while trying to open /dev/sdf1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

On another thread I found this:

```
sudo mke2fs -n /dev/sdf1
```

This gave me the following:
```

mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
20021248 inodes, 40019915 blocks
2000995 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1222 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872
```


Can anyone help me? I don't mind a new install, but there's some really important data on that home partition. The crash occurred just before my daily backup.

edit:
I've jsut tried fdisk:
```

Disk /dev/sdf1: 163.9 GB, 163921572864 bytes
255 heads, 63 sectors/track, 19928 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01000100

Disk /dev/sdf1 doesn't contain a valid partition table

```

---

### Post by Daelyn on 2008-01-21
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Try using that program. It should be able to rewrite the partition without loosing any data, but, I've not tested it myself, so I do not give any guarantees here.

---

