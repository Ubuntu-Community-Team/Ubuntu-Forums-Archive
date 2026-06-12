---
title: "Failed Gparted resize"
date: 2012-11-11
forum: Hardware
---

### Post by costansin on 2012-11-11
I had installed my ubuntu to a too small partition - it permitted me even to install programs, I had to clean up or move to another partition all the movable files. Sometimes it wrote there was 0 bytes of free space. In that case it permitted even to edit text files (but root could do it). Yesterday I decided to shrink and move all other partitions to enlarge the ubuntu one. All operations completed successfully except the last one - the ubuntu partition enlargement from 6 GiB to 46 GiB.
I've tried to save logs, but the LiveUSB system started to open/close nautilus, to output constantly (even after reboot) strange strings into console e.g. of tty5 (I mean this one, which I see, pressing Ctrl+Alt+F5)
I booted the main ubuntu system and found out that there were only 105 MiB of free space! But it should have been something about 40 GiB!
Now I've booted the LiveUSB system. It stopped outputing this stuff. I've mounted the ubuntu partition to /mnt/ and found out that it
Contents: 178,039 items, totalling 3.2 GB
(some contents unreadable)
Volume: unknown
Free space: 107.2 MB

What should I do? How to clean up all these 43 GB from nothing, I mean enable them to be used?

P.S. Disk utility shows 327730 bad sectors, is it really that bad? How it's connected with the failed Gparted resize?

---

### Post by ibjsb4 on 2012-11-11
There is hope, testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

