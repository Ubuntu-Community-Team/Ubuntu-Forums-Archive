---
title: "Can't have overlapping partitions."
date: 2009-06-02
forum: Hardware
---

### Post by yawnmoth on 2009-06-02
I have a hard drive with one big partition (37.26 GiB) and a bunch of little ones (ranging in size from 28.00 KiB to 256.00 KiB).  I'm able to delete all the partitions save for one of the little ones - a 31.50 KiB partition.  Attempting to delete it in GParted gets me the following error:

```
Partition map has no partition map entry!
```

Since there's not much I can do about that error, at the moment (hence this post), I delete all the other partitions and try to reformat the now unallocated space with ntfs as the file system.  That gets me the following error:

```
Can't have overlapping partitions.
```

I then tried to do "sudo fdisk -l" and here's what I got:

```
Disk /dev/sdc: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

Any ideas?  Is the disk bad, maybe?  If so, that seems a little strange, given that I was able to read data off of it just a few moments ago.  Indeed, the only reason I'm reformatting it is to reinstall my OS.

Also, why would there be so many partitions on the drive?  I can understand maybe one for a boot manager but eight or so?  That doesn't make any sense to me.

---

### Post by yawnmoth on 2009-06-02
I tried to reformat another drive that had the same mysterious 31.50 KiB partition and was unable to do so.  As before, the data was accessible prior to my reformat attempt.

The drives are from Apple MacBooks, in case that matters.

In any event, I figured out a workaround - in GParted, go to Device -> Create Partition Table....  That deleted all the partitions in one fell swoop as opposed to my having to delete each one one-by-one.

---

