---
title: "Ubuntu 8.10 Alternate on FakeRAID"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by TrickerZ on 2009-03-12
System:
Opteron 8347HE 1.9GHz Quad core
Tyan S4980G2NR (NVRAID)
2x4GB Kingston ECC RAM
4x Hitachi 1TB drives
Pioneer BDR-203BK
Intel XPI9404PTL quad port 10/100/1000

raid drives: /dev/sda + /dev/sdb = /dev/mapper/nvidia_adklla (raid0, not exact name)
/dev/mapper/nvidia_adklla[1-2] are not created
one of the 4 drives is broken, so I'm trying to do raid0 first and then raid 0+1 when the new drive comes in.

I'm trying to install 8.10 64bit alternate CD.  The install seems to go fine, but upon boot, the root is not found.  I've tried mounting the partitions with another live CD and it does not show the partitions, only the main RAID drive.  Running fdisk shows only 1 of the partitions and not the swap and says the file table is GPT.  If I go back and run the alternate CD again, I do not see the partitions even doing dmraid -ay, but when partman runs it sees them, it somehow creates the nodes and I can mount them and see the data on them (if I don't have it reformat the partition).  I'm wondering if there's something I can do to my initramfs image to create the nodes, or if I should just wipe the drive and do the GUI install with the fakeraidhowto.  What does partman do to create the nodes?

I could not find anyone else with this problem.

---

### Post by TrickerZ on 2009-03-12
Using the GUI and doing the grub stuff manually does not help.  Parted shows the proper partitioning scheme, but the nodes never get created.  What the heck does partman do to create them?!  If I could just figure this out, I could add it to my initramfs and be done with it.

---

### Post by TrickerZ on 2009-03-12
I got it to work by changing the partition table to MSDOS instead of GPT.  Unfortunately this limits me to 2TB partitions, but it'll have to do until they fix this problem.

---

