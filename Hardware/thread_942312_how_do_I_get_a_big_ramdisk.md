---
title: "how do I get a big ramdisk"
date: 2008-10-09
forum: Hardware
---

### Post by excogitation on 2008-10-09
I'm trying to mount a jffs2 image and
found a nice explanation on how to do it here:
[Installing and Mounting JFFS2 (Journaling Flash File System version 2)]("http://ubuntuforums.org/showthread.php?t=432481")

The thing is that my jffs2 image is a lot bigger than 4MB.

> dd: writing to `/dev/mtd0': No space left on device
102401+0 records in
102400+0 records out
52428800 bytes (52 MB) copied, 0.555015 s, 94.5 MB/s


I tried
```
modprobe mtdram total_size=8192 erase_size=256
```
but I can't create a large enough ramdisk (~100MB) with it (although I have about 1.5GB free ram).

Is there a way to maybe increase the size of mtd0?

---

