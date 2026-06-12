---
title: "Webmin says Disk Failed - Which one is it?"
date: 2013-10-13
forum: Hardware
---

### Post by Casey_Friday on 2013-10-13
Webmin reports that a disk has failed, but I don't know how to check which it is.

This is a brand new system that I just installed today, and it might be saying it failed because I shut the system down while RAID was building, but all the four 2TB WD Reds have no data on them...

Any ideas why webmin would report one brand new drive dead?  And if so, how do I find out which one it thinks it is?

System: Ubuntu Server 12.04.3 LTS. Intel Celeron G1610 processor, 8GB ADATA RAM, OS on Patriot USB2 Flash Drive, storage = four WD Red 2TB drives.

---

### Post by Casey_Friday on 2013-10-14
Well, it turned out that once the rebuild was finished (even though I guess I didn't let it run in the first place?) webmin now says all disks are healthy and active.  It must have been the initial build of the RAID5 array - I just didn't know that would take more than a couple seconds, since there is no data on any of the drives.

I guess I'll need to read more into how RAID works!

---

