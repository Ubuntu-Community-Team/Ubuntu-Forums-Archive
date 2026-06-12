---
title: "gparted fails to recognise parition table after installing XP via Virtualbox onto HDD"
date: 2011-11-18
forum: Hardware
---

### Post by _Ouroboros_ on 2011-11-18
I recently installed Windows XP onto a partition via virtualbox, with Ubuntu being the Host OS.  I gave virtualbox access to the full real HDD so I could then reboot the real machine and hopefully have a fresh install of XP on the real machine.

Now when I boot into Ubuntu, everything boots fine and all partitions, including the encrypted root partition, are mounted at boot time.  The only problem is that when I open gparted, gparted fails to recognise any partition, as if there is no partition table :confused: (see image).

[IMG]http://img607.imageshack.us/img607/6118/gpartedfail.png[/IMG]

Is there any way one can fix this problem without corrupting the actual partitions and seemingly hidden partition table?  I am guessing that the program "testdisk" may be able to fix this problem, but I have never had to repair a partition table before so here I am asking for help ... I do not want to try a solution with testdisk and be left with a system that does not even boot.

Partitions mount at boot fine, so I am guessing the partition table is intact, but just somehow hidden from gparted.  I don't know.

---

