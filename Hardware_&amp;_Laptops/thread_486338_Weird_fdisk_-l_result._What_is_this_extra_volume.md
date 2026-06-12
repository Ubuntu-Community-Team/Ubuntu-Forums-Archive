---
title: "Weird fdisk -l result. What is this extra volume?"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by samuraiCat on 2007-06-27
Hey guys, as I was using fdisk-l on a different matter, I got this weird result. Can anyone tell me what this phantom 131MB sdb drive is?

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649       10943    58597087+  83  Linux
/dev/sda3           10944       11490     4393777+  82  Linux swap / Solaris
/dev/sda4           11491       30401   151902607+  83  Linux

Disk /dev/sdb: 131 MB, 131072000 bytes
5 heads, 50 sectors/track, 1024 cylinders
Units = cylinders of 250 * 512 = 128000 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     3112544     7678583   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(3112543, 3, 9)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(7678582, 0, 39)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      674759     8418872   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(674758, 0, 23)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(8418871, 0, 12)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     7479526    15223639   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(7479525, 4, 16)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(15223638, 3, 7)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1    14548906  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(14548905, 4, 46)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


Say what?

---

### Post by merlinus on 2007-06-27
Is it possible that your computer manufacturer has placed a hidden recovery partition on your hard disk (e.g. dell, sony)?

When you look at your partitions using gparted, does this show up?

-merlin

---

### Post by samuraiCat on 2007-06-27
> **merlinus said:**
> Is it possible that your computer manufacturer has placed a hidden recovery partition on your hard disk (e.g. dell, sony)?

When you look at your partitions using gparted, does this show up?

-merlin

Okay, now I'm scared. It does not show up on gparted. Gparted shows everything as it should be.

This all started when I tried to mount a USB flash drive. I can't get it to mount or be recognized, and in the process of trying to figure that out, I found this result.

---

### Post by merlinus on 2007-06-27
It may simply be that the flash drive needs to be re-formatted.

Did you try loading it in windows?

-merlin

---

### Post by samuraiCat on 2007-06-27
> **merlinus said:**
> It may simply be that the flash drive needs to be re-formatted.

Did you try loading it in windows?

-merlin

Yes, it's fine in XP. BTW, to answer your earlier question, I built this system (with a little help from my brother), so there shouldn't be anything else on here.

I also noticed in gparted that it says that I have 233G total. This is a 250G drive. What is going on here?

---

