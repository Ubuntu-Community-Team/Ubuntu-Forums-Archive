---
title: "Re-Partitioning Vista"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by jprice148 on 2009-08-02
So I was installing a dual-boot with vista and Ubuntu 9.04. I recieved an error upon re-boot (it shown 2 boot files for Vista. One would load the OS and the other gave a fatal error). I believed that I had accidentally installed both OS on the same partition (and was incorrect) so I removed the 2nd partition. I Recieved the error 22 (no partition found) upon boot, so on so forth. I reset my MBR to get Vista operable and defragmented my disk with the Vista disk manager and a 3rd party and still do not have a enough space to re-partition the drive. I have a 120 gig HD with around 50 Gigs free....inititally it let me partition a max of around 36.5 GB and now only 2.5 GB. The 3rd party I used was MyDefrag. Should i try another defrag program or what? I am wanting to repartition and re-install Unbuntu. Any suggestions would be appreciated

---

### Post by merlinus on 2009-08-02
Use vista's disk management tool to shrink its partition.  Make sure to delete temp files and clean out temp directories, and defrag several times.

Also, you might disable the paging file, reboot and delete pagefile.sys, and then defrag.  There is no need to use third-party defraggers for this purpose.

Perhaps then the partition can be resized to a greater degree.

---

