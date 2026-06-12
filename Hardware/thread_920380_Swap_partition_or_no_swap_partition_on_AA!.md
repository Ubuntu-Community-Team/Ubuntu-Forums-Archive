---
title: "Swap partition or no swap partition on AA!?"
date: 2008-09-15
forum: Hardware
---

### Post by dada1958 on 2008-09-15
I have Ubuntu 8.04.1 running on my AA1 with 8 GB SSD and 512 RAM
I just read these guidelines on the Arch Linux on AA1 [site]("http://wiki.archlinux.org/index.php/Acer_Aspire_One") and this cite caught my attention:
> A110L: Avoiding Pitfalls for SSD version

Solid state drives are made of flash memory. They are fast in reading but slow in writing data. Flash memory you cannot overwrite countless times. So for a long ssd life take care to

   1. Never choose to use a journaling file system on the SSD partitions
**   2. Never use a swap partition on the SSD**
   3. Edit your new installation fstab to mount the SSD partitions "noatime"
   4. Never log messages or error log to the SSD At this moment I have a swap partition double the size of my RAM, so what's the best thing to do?

---

