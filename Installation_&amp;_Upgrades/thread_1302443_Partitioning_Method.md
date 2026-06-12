---
title: "Partitioning Method"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by Ubu-freak on 2009-10-27
I am seeking a nice partition method so I would like to see how some of you guys partitioned your ubuntu systems.
eg.
5G /home
5G for the rest
1G for swap

Also I would like to know where to install programs such as Matlab, Xilinx and stuff..(in /usr? /opt?)

---

### Post by TBerk on 2009-10-27
Half of the 250G HD is WinXP the other is Ubuntu.

Within the Ubuntu side of things I have about 12G given over to '/' ( it turns out that was excessive). I can get by with half of that, really.

Swap gets 2G although that too is turning out to be excessive. (I though rips and re-configs of large audio/video files might need it though...)

The rest, more than 100G is /Home for the most part. 

If I get around to installing a new HD (or wiping and reinstalling from scratch) I revisited what practical experience has taught me, until then this works fine.


berk

---

### Post by louieb on 2009-10-27
Kinda of extreme but I keep partitions for stable and testing installs, a dedicate Grub partition, swap, and a storage partition.


[LIST]
[*]Dedicated Grub - 25Mb
[*]Stable Install   - 15GB
[*]Test Install - 15GB
[*]Stable Home - 5GB
[*]Test Home - 5GB
[*]Swap - 1 GB
[*]Storage - whatever is left on the drive.
[/LIST]
Great for testing and checking out the new release that comes out every 6 months. And knowing i have a stable Install to boot to if testing gets screwed up.

---

