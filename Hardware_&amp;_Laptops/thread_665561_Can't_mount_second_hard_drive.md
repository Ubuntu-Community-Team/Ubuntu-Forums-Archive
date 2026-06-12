---
title: "Can't mount second hard drive"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by tobycatlin on 2008-01-12
Hi,
I bought a pair of 500gb drive recently and they have been working fine, except i haven't managed to get them to mount automatically. after the last reboot i went to mount them manually and i got an error message.

root@media-box:/home/toby# mount /dev/sdc1 /media/drive1
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

It was formatted with etx3 file system. I had a look at the partition with gparted which reports that about half the partition is full, which is right. I also ran through gparted check which came back ok but still won't mount.

fidsk returns the following:
toby@media-box:/home/toby# fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca2a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

So i ran demsg and got:

@media-box:/home/toby# dmesg | grep sdb
[  159.432938] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  159.432948] sd 2:0:1:0: [sdb] Write Protect is off
[  159.432951] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  159.432966] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  159.433004] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  159.433014] sd 2:0:1:0: [sdb] Write Protect is off
[  159.433016] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  159.433032] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  159.433035]  sdb: sdb1
[  159.438544] sd 2:0:1:0: [sdb] Attached SCSI disk
[  170.355567] VFS: Can't find ext3 filesystem on dev sdb.

I used testdisk and that found the data on the drive but i didn't know how to use it properly and don't want to wipe the data accidentally.

After nagging most people i know about the importance of regular backups i find myself caught with my pants down as all my christmas pictures are on that drive. Can anyone help me out, data recovery really isn't a trial and error kind of game.

thanks

toby

---

### Post by tobycatlin on 2008-01-12
hold up i am getting in a twist with my sdb and sdc

---

### Post by tobycatlin on 2008-01-12
ok it is /dev/sdc that has the problem.

fdisk reports:
@media-box:/home/toby# fdisk /dev/sdc -l

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004cc07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux


demesg says:
@media-box:/home/toby# dmesg | grep sdc
[  159.438588] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[  159.438597] sd 3:0:0:0: [sdc] Write Protect is off
[  159.438600] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[  159.438615] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  159.438649] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[  159.438659] sd 3:0:0:0: [sdc] Write Protect is off
[  159.438661] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[  159.438676] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  159.438679]  sdc: sdc1
[  159.441193] sd 3:0:0:0: [sdc] Attached SCSI disk
[  170.472409] VFS: Can't find ext3 filesystem on dev sdc.
[  707.624453] EXT2-fs error (device sdc1): ext2_check_descriptors: Block bitmap for group 640 not in group (block 33686636)!
[  912.672326] EXT2-fs error (device sdc1): ext2_check_descriptors: Block bitmap for group 640 not in group (block 33686636)!
[ 2215.342126] EXT2-fs error (device sdc1): ext2_check_descriptors: Block bitmap for group 640 not in group (block 33686636)!


which seems to suggest that the system thinks it's a ext2 file system.
anyone know what i can do from here?

ta toby

---

### Post by taurus on 2008-01-12
Can you mount it with

```
sudo mount -t ext2 /dev/sdc1 /media/drive1
```

---

### Post by tobycatlin on 2008-01-12
thanks for getting back to me.
i am mid way through a scan with testdisk so i'll give that a go when it's done. I am sure it was a ext3 partition though.

---

### Post by tobycatlin on 2008-01-12
i get 

@media-box:/home/toby# mount -t ext2 /dev/sdc1 /media/drive1
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by taurus on 2008-01-12
Try ext3 sine you said it's an ext3 filesystem.

```
sudo mount -t ext3 /dev/sdc1 /media/drive1
```

---

### Post by tobycatlin on 2008-01-12
Itried that and got the same message.
i tried gparted and that thinks it's ext2 and so tried the check and repair and it error right away with:

Check and repair filesystem (ext2) on /dev/sdc1  00:01    ( ERROR )
     	
calibrate /dev/sdc1  00:00    ( SUCCES )
     	
path: /dev/sdc1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
check filesystem on /dev/sdc1 for errors and (if possible) fix them  00:01    ( ERROR )
     	
e2fsck -f -y -v /dev/sdc1
     	
Group descriptors look bad... trying backup blocks...

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device&gt;

e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

Is there a way to find out my backup superblock and restore it with e2fsck?

Thanks for the help i would hate to lose the data

---

### Post by tobycatlin on 2008-01-13
I think i have found some backup super blocks using mke2fs. Problem is the search returned several results.
```

toby@media-box:~$ sudo mke2fs -n /dev/sdc
[sudo] password for toby:
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61063168 inodes, 122096646 blocks
6104832 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000


```

So i should be able to run something like:
e2fsck -b 32768 /dev/sdc1

How do i know which super block to use?
Will it matter which one i use. 

Thanks for any help. I am pretty sure this is the righht thing to do but i don't want to make things worse.

---

### Post by tobycatlin on 2008-01-14
I ran:
e2fsck -b 32768 /dev/sdc1

With various different super block values and they all gave the same error:

@media-box:~$ sudo e2fsck -b 32768 /dev/sdc1
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;


Is it possible that it is a ext3 file system that has been corrupted and now gparted and other utils now think it's ext3

---

### Post by vanadium on 2008-01-14
Shouldn you have performed the "sudo mke2fs -n /dev/sdc" on the partition instead, i.e. substitute /dev/sdc1 rather than /dev/sdc?

---

### Post by tobycatlin on 2008-01-14
mke2fs does return a list of backup superblocks 
```

toby@media-box:/media/disk$ sudo mke2fs -n /dev/sdc1
[sudo] password for toby:
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61063168 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000

```

but when i try to use them with e2fsck eg 
e2fsck -b 32768 /dev/sdc1
or
e2fsck -b 20480000 /dev/sdc1
all give the error in my previous post.

---

### Post by tobycatlin on 2008-01-14
does this information help?
```
toby@media-box:~$ sudo dumpe2fs -h /dev/sdc1
[sudo] password for toby:
dumpe2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          cbec84f5-d2fc-4799-8dbc-515da6732ee4
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61063168
Block count:              122096000
Reserved block count:     6104800
Free blocks:              26696892
Free inodes:              68990491
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Last mount time:          Sun Nov 11 21:36:37 2007
Last write time:          Sat Jan 12 19:05:30 2008
Mount count:              37
Maximum mount count:      30
Last checked:             Thu Jan  1 01:00:00 1970
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
ext2fs_read_bb_inode: Illegal doubly indirect block found

```

and

```

toby@media-box:~$ sudo lde /dev/sdc1
User requested autodetect filesystem. Checking device . . .
Found ext2fs on device.
lde_seek_block: seek failed, errno=22
Read error: unable to seek to block0x81bf4d04 in nocache_read_block, errno=22
lde: EXT2_read_tables: read failed in EXT2_read_inode_bitmap

```

---

