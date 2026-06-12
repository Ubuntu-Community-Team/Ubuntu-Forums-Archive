---
title: "Partition help"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Sayitall on 2009-02-12
Let me preface this by stating that I pretty much have no idea wha I'm doing. That said.. So I was in the process of partitioning with 40G Ubuntu, 120G Vista when a 'partitioning aborted' error message appeared and I ended up where I am. 

I am given the option 'Prepare partitions' of which I have 1572MB /dev/sda1, 158432 MB /dev/sda2 and 32 MB free space. I'd like to eventually be able to dualboot ubuntu and windows. 
Can anyone tell me how to manually set up these partitions?

---

### Post by Dies on 2009-02-12
I'm sorry, you got an error during partitioning, does this mean you can no longer boot Vista?

Assuming you can still boot vista, use the Vista utility to shrink the Vista partition, then boot the Ubuntu CD and use gparted to make your new partitions.

---

### Post by Mark Phelps on 2009-02-12
Dies is correct -- be sure to use Vista to shrink the Vista OS partition.

If you use Ubuntu or GParted, you run the risk of corrupting the Vista OS boot, which can only be repaired by booting from a Vista DVD and running Startup Repair.

You DO have a Vista DVD, right?

---

