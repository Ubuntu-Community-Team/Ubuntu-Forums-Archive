---
title: "Raid 0 Unable to Seek on /dev/sda and broken GRUB"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by JCoster on 2008-12-24
Hi.  I have finally managed to install Intrepid onto my Intel Raid0 array as a partition of array.  On the other partition is Vista.

I installed using the alternate CD and it detected free space and existing partitions, and even when it got to GRUB it detected previous Windows installs.

I therefore told it to write the Windows installs to the loader but upon boot only the default 3 Ubuntu options showed.

Ubuntu loads fine and so upon trying to do an fdisk -l as root, I get the following error:
"Unable to seek on /dev/sda"

If I run sfdisk -l on /dev/sda I get the following:
```
Disk /dev/sda: 36481 cylinders, 255 heads, 63 sectors/track
lseek: Invalid argument

sfdisk: seek error on /dev/sda - cannot seek to 1039019940
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    911     912-   7325608+  12  Compaq diagnostics
/dev/sda2   *    912+  64675-  63764- 512180220    7  HPFS/NTFS
/dev/sda3      64676   72960    8285   66549262+   5  Extended
/dev/sda4          0       -       0          0    0  Empty

```

Where sda2 is my Windows install and sda3 is my Ubuntu partition.

However, since I cannot run fdisk -l I cannot find out the hard disk partition of Vista, i.e. hd(0,2) or whatever.  The Ubuntu partition is hd(0,4) taken from /boot/grub/menu.lst.

Any ideas? I'm starting to think it may be a problem with my partition tables.

Also, if I run the application 'testdisk' it sees my drives independantly rather than in the raid0 array.  Is this a problem?  I have not run it yet as I believe it should see it as one big disk?

Thanks in advance.
JC

---

### Post by JCoster on 2008-12-24
Sorry to double post but just to add that when I attempt to run 'cfdisk /dev/sda' I get the error: *FATAL ERROR: Bad primary partition 1: Partition ends after end-of-disk*

Thanks

---

