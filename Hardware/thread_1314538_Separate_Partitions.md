---
title: "Separate Partitions"
date: 2009-11-04
forum: Hardware
---

### Post by kakashi_12 on 2009-11-04
I'm going to dual boot my new computer with Windows and Linux. I would create 1 partition for the Linux OS, 1 partition for the Windows OS, and then 1 or 2 other partitions for my files.

Could I be able to put both Windows and Linux files on the same partition; as long as I made a separate folder for each in the root of the drive (one called linux and another called windows)?

---

### Post by howefield on 2009-11-04
> **kakashi_12 said:**
> I'm going to dual boot my new computer with Windows and Linux. I would create 1 partition for the Linux OS, 1 partition for the Windows OS, and then 1 or 2 other partitions for my files.

Could I be able to put both Windows and Linux files on the same partition; as long as I made a separate folder for each in the root of the drive (one called linux and another called windows)?

The easiest way for both operating systems to access the shared data storage partition would be to format it as ntfs.

Also think about making a seperate partition for your Ubuntu /home as this may make reinstalling if required in the future easier.

A sample partition layout could be

1 x Windows ntfs
1 x Ubuntu / ext3/4
1 x Ubuntu /home ext3/4
1 x Ubuntu Swap
1 x Shared partition ntfs

---

