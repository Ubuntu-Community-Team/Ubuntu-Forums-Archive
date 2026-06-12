---
title: "Hard Drive Troubles"
date: 2008-08-31
forum: General Help
---

### Post by TreeFinger on 2008-08-31
Today I attempted to boot my ubuntu partition. fsck said it needed to be run because fs was mounted 29 times.

fsck received errors, computer rebooted.

For a few times I rebooted it took my bios a time longer than normal to detect the hard drive (i only have 1 hard drive). Now the bios is detecting the hard drive at a normal speed, but both my windows and ubuntu partitions are acting up.

My windows partition runs super slow.. something is definitely wrong.

Right now my ubuntu partition will only mount in read-only. I can't save files anywhere. I can't run apt-get

```

~$ sudo apt-get remove wine
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

Last thing I installed yesterday was Wine, so I'm thinking that has messed up both my windows and ubuntu partitions.. I'm trying to run fsck but I keep getting errors there also..

```

$ fsck -ACV -r
fsck 1.40.8 (13-Mar-2008)
Checking all file systems.
[/sbin/fsck.ext3 (1) -- /] fsck.ext3 -r -C0 UUID=08dcbe48-fe8b-4fe4-b41a-a9269a36b327 
fsck.ext3: Unable to resolve 'UUID=08dcbe48-fe8b-4fe4-b41a-a9269a36b327'
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=08dcbe48-fe8b-4fe4-b41a-a9269a36b327 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=f3306671-c3ea-437c-9a00-f5a6f6dd4372 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
$ sudo vol_id /dev/sda4
[sudo] password for tree: 
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=08dcbe48-fe8b-4fe4-b41a-a9269a36b327
ID_FS_UUID_ENC=08dcbe48-fe8b-4fe4-b41a-a9269a36b327
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

What should I do?

--edit
```

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a368a36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       40794   276478650    7  HPFS/NTFS
/dev/sda3           40795       41037     1951897+  82  Linux swap / Solaris
/dev/sda4           41038       48641    61079130   83  Linux

```

---

### Post by tjwoosta on 2008-08-31
installing wine should not effect your hard drive


it sounds to me like it may just be that your harddrive is going bad

how old is it?

---

