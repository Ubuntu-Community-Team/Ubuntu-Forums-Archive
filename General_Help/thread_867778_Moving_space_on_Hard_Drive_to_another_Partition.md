---
title: "Moving space on Hard Drive to another Partition"
date: 2008-07-23
forum: General Help
---

### Post by Paul Earland on 2008-07-23
Having deleted XP from my hard drive using gparted, I now have an unallocated Partition with 7.71GB of space. Also on my Hard Drive I have a Fat 32 Partition where I store all of my work, but with a total of 3.99GB of total space I only have 683 MB free. Can I transfer and how, the 7.71GB of free space from my old XP Partition to my "Work" partition?
Thanks.
Paul

---

### Post by Potatoj316 on 2008-07-23
You should be able to expand existing partitions, but backup important files first, it probably wont but could damage some of them.

---

### Post by Elfy on 2008-07-23
Use your livecd - the partition editor is in system - admin

Couple of points - the partition you want to resize and the unallocated space (once you have deleted the old xp) need to be next to each other - which could mean that you have to move other partitions.

If any of the partitions you need to move about include the extended partition that ubuntu makes it will probably be necessary to turn off swap.

Once you start moving partitions it can take a while - like hours or more.

Don't decide it's hung and turn it off.

Good luck.

---

### Post by Paul Earland on 2008-07-23
> **forestpixie said:**
> Use your livecd - the partition editor is in system - admin

Couple of points - the partition you want to resize and the unallocated space (once you have deleted the old xp) need to be next to each other - which could mean that you have to move other partitions.

If any of the partitions you need to move about include the extended partition that ubuntu makes it will probably be necessary to turn off swap.

Once you start moving partitions it can take a while - like hours or more.

Don't decide it's hung and turn it off.

Good luck.

Thanks to all who came back to me. Took the easy way out and just called the spare partition WORK 2 and hopefully now have the choice of loading work to WORK 1 or WORK 2! I never use the inbuilt files such as MY Music or Documents etc. Always make my own folders and store them in a separate Work partition.
Thanks.
Paul

---

