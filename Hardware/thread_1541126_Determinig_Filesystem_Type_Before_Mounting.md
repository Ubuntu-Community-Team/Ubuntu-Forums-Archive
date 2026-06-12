---
title: "Determinig Filesystem Type Before Mounting"
date: 2010-07-28
forum: Hardware
---

### Post by colli419 on 2010-07-28
Hi all:

I would like to be able to ascertain the filesystem type for a partition of which I have no idea. Is this possible? I attempted to do this with a number of trial and error attempts using the mount command specifying types. They show up in the /dev folder so I know they are there, but I am not sure what to do from there. Any help or direction would be most helpful.

Thanks!

---

### Post by georgemc on 2010-07-28
I use "blkid" in my scripts.  See "man blkid"

```

sudo blkid -s TYPE -o value /dev/sdXY

```Replace the X and Y with the device and it should give you what you are looking for.  Cant remember if it is installed by default, if not use "apt" or "synaptic"

George

---

### Post by CharlesA on 2010-07-28
Running this:

```
sudo fdisk -l
```

Will tell you the device names and what file systems are on them.

---

### Post by colli419 on 2010-07-28
Thanks guys for the response. I pasted the output below but I have to say that it is not quite helpful yet. The first suggestion of using blkid only works on the first partition, not the second. Whereas the fdisk command does read both partitions, it does not give the same output as the first command. Also, reporting that "Linux" is the filesystem is not helpful for mounting as I was hoping for something a bit more specific. Ideas? Thanks!

```
mike@media-plox:~/Desktop$ sudo blkid -s TYPE -o value /dev/sdd1
ext2
mike@media-plox:~/Desktop$ sudo blkid -s TYPE -o value /dev/sdd2
mike@media-plox:~/Desktop$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4658    37415353+  83  Linux
/dev/sda2            4659        4863     1646662+   5  Extended
/dev/sda5            4659        4863     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7297    58613121   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x064c3c97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         125     1004031    c  W95 FAT32 (LBA)
/dev/sdc2             126       30401   243191970   83  Linux

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         125     1004031    c  W95 FAT32 (LBA)
/dev/sdd2             126       30401   243191970   83  Linux

```

---

