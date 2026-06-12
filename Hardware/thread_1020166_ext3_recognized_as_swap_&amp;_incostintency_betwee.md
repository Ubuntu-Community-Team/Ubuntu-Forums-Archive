---
title: "ext3 recognized as swap &amp; incostintency between vol_id, blkid and /dev/disk/by-uuid"
date: 2008-12-23
forum: Hardware
---

### Post by mgol on 2008-12-23
Recently, I messed up my partition table a little. I recovered it using testdisk, and 3 partitions (sdb1/3/4) per 4 all were properly recovered. However, /dev/sdb2 (containing my mp3s) has some problems.

All these partitions are mentioned in fstab. Here is a line connected to this sdb2 partition:
```

UUID=4067cb4d-59b7-4c35-9a8f-af1216b5d8de /media/mp3 ext3 defaults,user,noauto 0 0

```

But when I try to mount it, I get that:
```

$ sudo mount /dev/sdb2 /media/mp3
/dev/sdb2 looks like swapspace - not mounted

```

After giving the -t parameter:
```

$ sudo mount -t ext3 /dev/sdb2 /media/mp3

```
it's mounted properly, everything is readable etc.

I tried to check what's wrong using /dev/disk/by-uuid listing and blkid and vol_id programs; here is what I got:
```

$ blkid | grep sdb2
/dev/sdb2: LABEL="mp3" UUID="**4067cb4d-59b7-4c35-9a8f-af1216b5d8de**" TYPE="ext3" 
$ ls -l /dev/disk/by-uuid/ | grep sdb2
lrwxrwxrwx 1 root root 10 2008-12-24 03:35 **d3124f05-e83d-446e-b94c-f8e933bedc6f** -> ../../sdb2
$ vol_id /dev/sdb2
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=**ea4f5901-a8ae-8d01-0000-000002000000**
ID_FS_UUID_ENC=ea4f5901-a8ae-8d01-0000-000002000000
ID_FS_LABEL=
ID_FS_LABEL_ENC=\x02
ID_FS_LABEL_SAFE=_

```

As You can see, vol_id information is completely broken (including broken UUID etc.). blkid shows what should really be, I don't know why vol_id returns wrong info.

blkid, vol_id and /dev/disk/by-uuid returns 3 different UUIDs for this partition (in case of sdb1/3/4 they are all the same). blkid also returns info about /dev/sdb6 partition, which now does not exist.

How to repair this filesystem? What can be the reason of displaying different information for the same partition, using mentioned 3 methods?

Thanks in advance!

**P.S.** Maybe it's worth to mention that for /dev/sdb3 blkid returns an additional SEC_TYPE argument, which is not shown for sdb2:
```

$ blkid | grep sdb3
/dev/sdb3: LABEL="inne" UUID="1f5ed835-e8a9-4262-a88b-d71dae634c99" SEC_TYPE="ext2" TYPE="ext3"

```

**P.S.2** I've forgotten about this:
```

$ sudo fdisk -l /dev/sdb

(...)

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         131     1052226   83  Linux
/dev/sdb2             132       26108   208660252+  83  Linux
/dev/sdb3           26109       52216   209712510   83  Linux
/dev/sdb4           54175       60801    53231377+   c  W95 FAT32 (LBA)

```
As You can see, even fdisk claims that sdb2 is not swap-typed, although vol_id reports that.

---

### Post by taurus on 2008-12-23
What does this command display regarding your harddrive?

```
sudo fdisk -l
```

---

### Post by mgol on 2008-12-23
> **taurus said:**
> What does this command display regarding your harddrive?

```
sudo fdisk -l
```

I've pasted part of this at the end of my first post. This is all (I assume only /dev/sdb disk is interesting, as with my /dev/sda everything is OK):

```

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         131     1052226   83  Linux
/dev/sdb2             132       26108   208660252+  83  Linux
/dev/sdb3           26109       52216   209712510   83  Linux
/dev/sdb4           54175       60801    53231377+   c  W95 FAT32 (LBA)

```

---

