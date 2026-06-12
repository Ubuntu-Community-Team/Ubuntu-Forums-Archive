---
title: "external (sata) drive verification on coming back from sleep?"
date: 2013-03-13
forum: Hardware
---

### Post by erdelyi on 2013-03-13
This post is actually a feature request :idea
I boot Xubuntu (12.04) on my laptop from an external SATA drive (the internal one is for coprorate use, Xubuntu is the OS for my private use).

Sometimes I send my laptop (Lenovo T420) to sleep
Accidentally it can happen that I do not connect the cables (eSATA/USB for power) before trying to wake up the system.
It is no surprise that in these cases the operating system does not work and complains about device status change and issues reading inodes, superblocks (I have ext4 file system on the partition with the root file system). Unfortunately even after connecting the cable correctly, the system remains in this unusable state.

I would appreciate if there was some kind of "mount verification" -- polling the disk after it became unavailable, at least remounting it read-only after it becomes available -- not to endanger anyone with any other scenario --, with the possibility to remount read-write as root (when I know the issue was a not correctly plugged cable) 8-)

I guess this is independent of variants so I have chosen the [all variants] prefix...

---

