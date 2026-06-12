---
title: "dualbooting ubuntu and vista"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by fbp90crx on 2009-06-07
I'm wanting to put ubuntu on family PC so I was wanting to dualboot to see if they would like it over vista. I'm wanting to build a Ubuntu partition with Ext4 and a swap, what is the best way to do that?

---

### Post by merlinus on 2009-06-07
Use vista's disk manager to shrink its partition and leave room for ubuntu.  Defrag first, though.

Then during installation you can set up partitions for / (root - the ubuntu filesystem), swap, and /home.  You will be able to format them with ext3 or ext4.

Do a search for partitioning and you will find lots of good info.

---

### Post by Mark Phelps on 2009-06-07
Second what merlinus said ... and want to emphasize that you use the Vista Disk Management tool to shrink the Vista OS partition.  If you use the Ubuntu partitioner or a GParted LiveCD, you run the risk of corrupting your Vista installation so that it's not bootable anymore.

---

