---
title: "Hibernation not working after modifying hard disk partitions on Inspiron 6000"
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by jyap on 2006-02-24
I'm running a dual-boot on my laptop, Windows XP and Ubuntu 5.10.

I decided to create a FAT32 partition that I could share between the two.

In my previous setup:
```

<file system>,  <mount point>,  <type>
/dev/sda2       /media/c        ntfs
/dev/sda5       /               ext3
/dev/sda6       none            swap

```

In my current setup:
```
<file system>, <mount point>, <type>
/dev/sda2       /media/c        ntfs
/dev/sda5       /media/share    vfat
/dev/sda6       /               ext3
/dev/sda7       none             swap

```

As you can see, I reduced the size of the  NTFS partition and created the the Share partition /dev/sda5 which bumped up the Linux and Swap partition.

My problem is, now hibernation doesn't work in Ubuntu.  It just shuts down the machine and when I start it up, it's a total boot up.

I'm sure it's a simple problem to fix.  Any ideas/help?

.. Then again, I could just make my Share partition a Primary partition.

Thanks! :cool:

---

