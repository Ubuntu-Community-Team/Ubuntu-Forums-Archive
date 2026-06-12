---
title: "Very Excessive Hard Disk Activity"
date: 2010-07-02
forum: Hardware
---

### Post by redwoodguy on 2010-07-02
Ubuntu 10.04 (also happened on 9.10)
Gateway SX2802 w/Intel Q8300 processor, 4GB RAM, 750GB Seagate ATA

PROBLEM:
The hard disk is perpetually reading and writing even when there are no apps running. It is nearly constantly reading and writing, but will stop for 10 or 20 seconds and then go off again reading and writing. No pattern, all very random. 

I tried disabling the 9GB swap partition with Gpart. That seemed to have reduced it a little. But, what on earth is this disk doing if there is no applications running?

When I first installed 9.10 on this computer 7 months ago, I didn't notice this disk activity. Suddenly it appeared. I thought by upgrading to 10.04 it might go away. Nope. It's right back again. 

I fear the drive will simply wear itself out.

---

### Post by movieman on 2010-07-02
Install iotop and it should show you which programs are accessing the disk.

---

