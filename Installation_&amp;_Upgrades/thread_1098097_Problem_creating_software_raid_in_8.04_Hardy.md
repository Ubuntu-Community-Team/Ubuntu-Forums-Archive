---
title: "Problem creating software raid in 8.04 Hardy"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Erik-NA on 2009-03-16
When installing Ubuntu 8.04 64 server edition and setting up software raid 1, the md0 device is already setup when creating the first raid volume. It consists of only one partition, sda0 and cannot be removed, "already in use"

This is very strange since I have set up the following partitions.

Disk 1
4GB physical volume for raid, non bootable
70GB physical volume for raid, bootable

Disk 2
4GB physical volume for raid, non bootable
70GB physical volume for raid, bootable

After entering the meny "set up software raid" and selecting create md device with 2 physical volums, sda0 is not available. If I go back to the partioner, one 4GB software raid volume md0 is already created.

If I try to delete md0 I am getting an error saying it may be in use. 

What is the problem?

---

