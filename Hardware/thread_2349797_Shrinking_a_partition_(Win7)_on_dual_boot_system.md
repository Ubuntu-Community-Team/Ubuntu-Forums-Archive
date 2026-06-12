---
title: "Shrinking a partition (Win7) on dual boot system"
date: 2017-01-18
forum: Hardware
---

### Post by jerry50 on 2017-01-18
I have a dual boot laptop with Win 7 and Ubuntu 14.04.  I want to shrink the Win 7 partition because I need/want more space for the Linux side of things.  I went to G Parted and it shows 4 partitions with 2 that are below (belong to)  one of the partitions:

1.  /dev/sda1 which is an ntfs file system with a label that says System Reserved 100MB and a flag that says boot,  24.67MB used.

2.  /dev/sda2 also ntfs, 365.7 GB, 54.24 GB used.

3.  /dev/sda3 with a little key beside it, file system extended, with two other file systems under it, which are:

     4./dev/sda5 with a different kind of key beside it, ext4 File System,  96.16 GB, 90.24 GB used.

     5.  /dev/sda6 with key beside it like above, linux-swap File System, 3.80GB, 0.00 used.

6.  unallocated with unallocated File System, 1.02 MB.

**My question is, I've started shrinking the ntfs file (not the boot one), and it shows "1 operation pending" at the bottom of the screen.  ****[B]I'm shrinking it from 365 GB to 58 GB.  **How long does this take?  And is there anything to do but wait for this to end?  
[/B]

---

### Post by jerry50 on 2017-01-18
Never mind.  I didn't know that there was a final step to start the operation.  :)

---

