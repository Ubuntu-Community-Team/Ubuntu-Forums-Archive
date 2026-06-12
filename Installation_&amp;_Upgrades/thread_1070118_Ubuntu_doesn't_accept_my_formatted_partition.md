---
title: "Ubuntu doesn't accept my formatted partition"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by commanderriker on 2009-02-14
So I have a disk of which I have installed Ubuntu before, but now if I try to install onto a partition of my new hard drive, it gives me an error message stating "No root file system defined. Please correct this in the partitioning menu." Despite the fact that I made the partition in the partitioning menu of ubuntu setup, and I'm using the ext3 file format, it still won't accept it. I was able to install it before by using an entire disk option. I don't want to do that, because I have Vista on one and large amounts of valuable data on the other, which has three partitions totaling 1 terabyte. I have one empty partition which was the one I was hoping to install ubuntu on, but I can't. Any ideas of what I could do? The hard drive is a Samsung spinpoint F1, which is 1 TB, 7200 RPM, 32 MB cache. I'm running a Compaq Presario SR5233WM, with a Pentium D 915 (dual core, 2.8GHz) and 2 GB of DDR2 RAM @ 667 MHz, etc.

---

### Post by dcstar on 2009-02-14
> **commanderriker said:**
> So I have a disk of which I have installed Ubuntu before, but now if I try to install onto a partition of my new hard drive, it gives me an error message stating "No root file system defined. Please correct this in the partitioning menu." Despite the fact that I made the partition in the partitioning menu of ubuntu setup, and I'm using the ext3 file format, it still won't accept it. I was able to install it before by using an entire disk option. I don't want to do that, because I have Vista on one and large amounts of valuable data on the other, which has three partitions totaling 1 terabyte. I have one empty partition which was the one I was hoping to install ubuntu on, but I can't. Any ideas of what I could do? The hard drive is a Samsung spinpoint F1, which is 1 TB, 7200 RPM, 32 MB cache. I'm running a Compaq Presario SR5233WM, with a Pentium D 915 (dual core, 2.8GHz) and 2 GB of DDR2 RAM @ 667 MHz, etc.

**You** have to select the "/" mount point on the partition.

---

