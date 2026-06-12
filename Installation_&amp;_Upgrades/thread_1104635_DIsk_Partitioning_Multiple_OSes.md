---
title: "DIsk Partitioning: Multiple OSes"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by TheHarbinger on 2009-03-23
I've installed XP SP3 on my laptop's hard drive, and used the disk manager to make multiple partitions with the goal of multi-booting XP, Ubuntu, and a Hackintosh install.  I've made 20 GB available each for Ubuntu and Hackintosh, and there's a small (10GB) FAT32 DOS partition available to all OSes as a common file swap partition. The rest of the disk is an NTFS logical drive for XP.

I went to install Ubuntu, and got into disk partitioning.  I pointed the partitioner to one of the 20 GB partitions, and told it to use that partition as the \ mount point.  I then got a dire message saying that I hadn't named a swap partition and this would cause problems.

Can't I simply install Ubuntu to that partition and have it subdivide the partition as it needs to, using part of it for a swap drive? Or will I have to re-do my entire disk partitioning scheme for an additional swap partition?

---

### Post by x33a on 2009-03-23
you'll have to make a separate swap partition.

you can reduce the size of ubuntu partition and allocate the rest to swap, depending upon your ram.

---

