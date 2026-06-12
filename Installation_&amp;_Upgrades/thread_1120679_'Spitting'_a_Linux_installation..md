---
title: "'Spitting' a Linux installation."
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-09
During installation you have to specify where you have to install Linux...the partition.

You have the freedom to install different directories of Linux in different partitions right?




Got very confused so clearing it from the beginning.


Oh...sorry for the subject...its 'splitting'.:lolflag:

---

### Post by mozetti on 2009-04-09
Yes, if you'd like you can put every major directory in its own partition: / (root), /var, /opt, /usr, /home, etc.

For most normal installations, you should probably only worry about giving / (root) and /home their own partitions. /home is generally used to store all of your data files and settings for programs. If you re-install the OS (to / (root) then you can re-use your /home partition and keep all your data and settings.

The tricky part about using different partitions for more directories than that is using the correct size. For example, I don't even know how large any of them "should" be - I just know that 6-8GB for /root and however large you want your /home (data) partition to be. 

Some directories won't grow much at all, so if you make it too large then you're just wasting space. Some directories will fluctuate and grow from log messages, software installation, etc. If you don't make those large enought then you run out of room.

Hope that helps.

---

### Post by dE_logics on 2009-04-09
> If you re-install the OS (to / (root) then you can re-use your /home partition and keep all your data and settings.

But setting were in the etc folder...:shock:

> The tricky part about using different partitions for more directories than that is using the correct size. For example, I don't even know how large any of them "should" be - I just know that 6-8GB for /root and however large you want your /home (data) partition to be.

Yes, that's why I'll monitor the sizes for the initial installation, then change it later on.

> Some directories will fluctuate and grow from log messages

We can delete those right?...logs only.

---

