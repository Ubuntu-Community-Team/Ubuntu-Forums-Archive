---
title: "Error creating file system"
date: 2010-05-08
forum: Hardware
---

### Post by lazyworkhorse on 2010-05-08
I have a 200GB internal IDE drive in my computer. I tried to reformat it and install windows(for netflix), but since my disk would not boot, I tried to reformat the entire drive as ext3, and got this error:

```

Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.9 (22-Aug-2009)
Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir 

```This disk worked perfectly just an hour ago, what happened and what do I do?

---

### Post by lazyworkhorse on 2010-05-09
Today I tried to delete all partitions. At first it went and then ave me an error. Now I get this instantly: 
```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=32256
Entering MS-DOS parser (offset=0, size=200049647616)
read failed (Input/output error)
Exiting MS-DOS parser
Entering Apple parser
read failed (Input/output error)
Leaving Apple parser
No known partition table found
got it
Error: /dev/sda: unrecognised disk label
ped_disk_new() failed

```

after its been running awhile, it makes a steady "chugging" (it reminds me of a train). It's a steady patern of 7, 3, 2 chugs/taps/ noises and when I was trying to write it earlier, it made a sort of chime sound.

---

### Post by lazyworkhorse on 2010-05-15
anyone?

---

