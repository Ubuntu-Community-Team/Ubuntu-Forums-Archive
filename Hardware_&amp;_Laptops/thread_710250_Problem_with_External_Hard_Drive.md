---
title: "Problem with External Hard Drive"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by Hydem on 2008-02-28
Hi there,

Some months ago I bought a Freecom 250GB external HDD. I plug it into my computer via USB. It has been working fine until yesterday when I turned on my computer and the icon on the desktop (which normally appears when the device is plugged in and working doesn't appear. I have been looking around the forums and I haven't found any information that has helped me clear my problem. I tried the following stuff:

fdisk -l
```

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48a41580

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)

```

I think this means it is plugged in and on but it still doesn't recognize it.

The contents of my fstab file are:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4122afc9-e577-4d6f-b927-1e7d071b6733 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=760b725a-6354-4d2a-8d16-86a913a38de9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

I hope this helps you to help me. Any other information you need & I can provide just tell me.

Edit: Also, when I try (although I don't know if this is correct at all)```
sudo mount -t vfat /dev/sdb /media/sda1
```

I get this:```
wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

When I try dmesg | tail I get:```
[ 2309.752000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[ 2309.912000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[ 2309.912000] SGI XFS Quota Management subsystem
[ 2309.924000] XFS: bad magic number
[ 2309.924000] XFS: SB validate failed
[ 2309.928000] XFS: bad magic number
[ 2309.928000] XFS: SB validate failed
[ 2309.968000] JFS: nTxBlock = 4027, nTxLock = 32223
[ 3069.340000] FAT: invalid media value (0xb9)
[ 3069.340000] VFS: Can't find a valid FAT filesystem on dev sdb.

```

Hope it helps.

Thanks in advance,

---

### Post by taurus on 2008-02-28
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by Hydem on 2008-02-28
That has to be the fastest response ever. Thanks a lot, I can now access my hard drive.

One last question, do I have to follow any procedure to unmount it before I turn it off now or? Before I used to right-click on it and select "unmount volume" but the icon is no longer on the Desktop so that's not an option?

Thanks again for the fast response,

---

### Post by taurus on 2008-02-28
You can unmount it from a terminal before you unplug or power it off if you wish.

```
sudo umount /media/sdb1
df -h
```

---

### Post by Hydem on 2008-02-28
Thanks once again,

---

