---
title: "gparted, &quot;round to cylinders&quot;, and free space"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by marshmallow1304 on 2009-10-30
I'm getting ready to install Karmic for the second time (test run on my desktop worked nicely).  Before I do, I want to increase the size of my / by giving it space from my /home partition.  Then during install, I'll format / to ext4 and set the other partition to mount as /home.

So, I booted up the Live CD and opened gparted.


However...

If I put more free space before my /home and leave "round to cylinders" checked, I always end up with 2.49 MiB unallocated space at the end of the disk.  If I uncheck "round to cylinders", there's no problem.

Basically, is it OK to uncheck "round to cylinders", or is it important that I leave it checked?

---

### Post by lisati on 2009-10-30
I'm not sure of all the details but suspect that it could be related to efficiency should you decide to set up multiple partitions. It's probably ok to leave it unchecked.

---

### Post by marshmallow1304 on 2009-10-30
Thanks for your reply, but I feel really stupid.  I didn't bother to finish setting up all the partitions before I created this thread.  Once I set all the partitions correctly, the unallocated space took care of itself.

D'oh

---

