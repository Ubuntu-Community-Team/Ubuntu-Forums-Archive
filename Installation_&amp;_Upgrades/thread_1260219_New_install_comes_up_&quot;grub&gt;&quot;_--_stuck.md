---
title: "New install comes up &quot;grub&gt;&quot; -- stuck"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by huffcs on 2009-09-07
I installed MythBuntu 9.04 to a 15GB test drive successfully.  Swapped for a 40GB disk to go production, but now it won't boot up completely.  It finds the MBR code and starts grub, but promptly goes to "grub>" prompt and stops.  I don't get any menu of kernels to choose from at all.

I mounted the /boot partition while running from the live cd and the contents look okay, but I don't know enough to do more than see that the grub/menu.lst exists and doesn't look patently corrupt.

I tried the find command at the grub> prompt and finally found /grub/stage1 on (hd0,0), which is what I would expect (although the thread I got the idea to try this from talks about finding /boot/grub/stage1 -- perhaps the difference is because I put /boot on its own partition?).

FWIW, the 15GB system was partitioned thusly:
/boot          98M    /dev/sdb1 (Primary)
/          11,852M    /dev/sdb5 (Logical)
swap     2,048M    /dev/sdb6 (Logical)
/var       1,019M    /dev/sdb7 (Logical)

And the 40GB drive was partitioned this way:
/boot         98M   /dev/sdb1 (Primary)
/         35,821M   /dev/sdb5 (Logical)
swap    2,048M   /dev/sdb6 (Logical)
/var      2,048M   /dev/sdb7 (Logical)

In both cases, the drive is identified by the live cd as /dev/sdb -- /dev/sda is a large SATA drive I use for storing MythTV recordings.  Both the 15GB and the 40GB drives are spare IDE drives I have available for putting the O/S and mysql repository on.

Any guidance gratefully accepted.

Craig.

---

