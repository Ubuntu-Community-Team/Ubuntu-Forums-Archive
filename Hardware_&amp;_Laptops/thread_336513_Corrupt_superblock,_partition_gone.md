---
title: "Corrupt superblock, partition gone"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by c0njur on 2007-01-11
Hi all,

After attempting to restore Windows using Acronis Backup, I realized that one of my partitions  is gone. While Ubuntu was loading, I got the following error message:

```
fsck.ext3: No such file or directory while trying to open /dev/hda2
/dev/hda2:
The superblock could not be read or does not describe a correct ext2 filesystem (and not swap or ufs or somethingelse), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
	e2fsck -b 8193 <device>
```

Using e2fsck -b 8193 /dev/hda2 I get this:

```
e2fsck 1.38 (30-Jun-2005)
e2fsck: No such file or directory while trying to open /dev/hda2
```

When I run fdisk -l I get this:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda3   *        8964        9601     5124735   83  Linux
/dev/hda4            9602        9729     1028160   82  Linux swap / Solaris
```

So in conclusion, is there any way to get my data back or am I totally screwed?

---

### Post by Sef on 2007-01-11
Check out [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

