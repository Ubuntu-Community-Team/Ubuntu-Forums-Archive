---
title: "Unknown filesystem 'linux_raid_member'"
date: 2009-03-27
forum: Hardware
---

### Post by kayec on 2009-03-27
Hi !!

I have a hard drive that was part of a mirror (ext2 file).  The device it was in (dLink 323) has broken down.

I'm running Ubuntu and can see the disk, even the partitions using GParted however i can't mount it.

Any suggestions on how to mount this sucker??

---------------------------------


[IMG]http://coreykaye.com/dns323-error1.png[/IMG]

---------------------------------
[IMG]http://coreykaye.com/dns323-error2.png[/IMG]

---------------------------------

---

### Post by gamez on 2012-01-18
A bit late, but the command is
> 
sudo mount /dev/sdXY /somewhere -t ext2


CU, gamez

---

### Post by kayec on 2012-01-18
> **gamez said:**
> A bit late, but the command is


CU, gamez

Thanks gamez!

---

