---
title: "Help with Partitioning before install of Ubuntu"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by Grantismo on 2009-02-20
Hi everyone,
I finally decided to partition my hard drive so I could give Linux a try. My computer's basic specs are:

Dell Latitude E6500
Intel(R) Core 2 Duo CPU T9400 @ 2.53 GHz
4.00 GB RAM
150 GB internal hard drive with ~54 Gigs free space
1 TB external hard drive, used to store media files
I'm currently Running Vista on my internal drive, and would like to dual boot.

I'm just trying to figure out how I should partition my internal drive. I heard that you should partition an additional 2*RAM GB for swap, and then ~10 GB for Ubuntu, does this seem appropriate? Other sources said that 1 GB could also be plenty for swap. I just need a little direction on this. Thanks in advance.

---

### Post by taurus on 2009-02-20
With 4GB of RAM, even 1GB is plenty.  So, go for 10GB for / and 1GB for swap.  I assume you will use the 1TB to share files between windows and Ubuntu.

Make sure you install the Ubuntu x86_64 version (64bit) if you want to use all 4GB of RAM.

---

### Post by wpshooter on 2009-02-20
The main thing is to make absolutely sure that you make a SEPARATE /home parition.

---

### Post by Grantismo on 2009-02-20
> **wpshooter said:**
> The main thing is to make absolutely sure that you make a SEPARATE /home parition.

Could you expand a little on that. I don't have much knowledge about Linux file hierarchy.

---

### Post by wpshooter on 2009-02-21
> **Grantismo said:**
> Could you expand a little on that. I don't have much knowledge about Linux file hierarchy.

Basically, you want 3 partitions.

If you don't plan on having any other O/Ss installed I would make all 3 of the PRIMARY partitions.

The 3 that you want are:

1) / = root partition for the O/S
2) /home = home partition for settings, personal use - other than O/S
3) /swap = swap partition for use when physical memory is exceeded

If you use the ALTERNATE version install make sure that you make the / root partition bootable - it is the last parameter on the partition information listing.

Good luck.

---

