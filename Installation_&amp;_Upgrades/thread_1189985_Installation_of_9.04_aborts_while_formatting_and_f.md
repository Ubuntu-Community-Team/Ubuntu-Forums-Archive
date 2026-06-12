---
title: "Installation of 9.04 aborts while formatting and falls back to live session"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Giacecco on 2009-06-17
Hi all,
I am trying installing Ubuntu 9.04 x86 desktop on a brand new Acer Veriton M670: an absolutely conventional mid-tower Intel Core 2 Quad vPro workstation. 

While performing the formatting of the root partition, the screen suddenly goes black and I find myself running Ubuntu as a live session. No error messages of any kind on screen.

The only strange behaviour I noticed is that the formatting takes too long, and sticks to 5% for a long time before triggering the unsolicited live session. 

It is not the first time I installed previous and this versions of Ubuntu but never had this problem. Any advice?

Giacecco

---

### Post by Mark Phelps on 2009-06-17
Yea -- Don't use the Ubuntu installer to do the formatting.  Instead, download and burn a GParted LiveCD from distrowatch.com, boot from that, and use it to create and format the partitions.

However, are any of the following true:
-- Your disk is already fully formatted with no unallocated space
-- You're trying to shrink an Vista (NTFS) partition
-- You're trying to install to an existing RAID setup
-- You're trying to install to a SSD (solid state drive).

If so, you're going to have real problems getting the install to work.

---

