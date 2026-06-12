---
title: "SparesMissing event with software RAID"
date: 2008-07-29
forum: Hardware
---

### Post by noisebar on 2008-07-29
I keep getting the following message every day or so.  Everything seems to be working fine regardless of it.  Any idea?

> Subject: SparesMissing event on /dev/md1:ubuntu
Date: Tue, 29 Jul 2008 08:59:46 -0600

This is an automatically generated mail message from mdadm
running on ubuntu

A SparesMissing event had been detected on md device /dev/md1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda3[0] sdb2[1]
      247465152 blocks [2/2] [UU]
      
md2 : active raid0 sda2[0] sdb1[1]
      125836928 blocks 64k chunks
      
unused devices: <none>

---

### Post by Bjorn Ruud on 2009-08-21
If it happens after a reboot, it might be this bug (solution provided):
[https://bugs.launchpad.net/bugs/252365](https://bugs.launchpad.net/bugs/252365)

---

