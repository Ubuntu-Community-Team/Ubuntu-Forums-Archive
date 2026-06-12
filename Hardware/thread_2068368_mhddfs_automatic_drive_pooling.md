---
title: "mhddfs automatic drive pooling?"
date: 2012-10-09
forum: Hardware
---

### Post by th3count on 2012-10-09
Hello, First post I recently started using Ubuntu for an XBMC HTPC. i really am enjoying it, much better then WMC:MB

my old media browser system took alot of work to get as automated as possible. What i am trying to achieve at the moment is automated drive pooling. at the moment i have 4 external drives strung together using mhddfs but i would really like to automate this so that when a new drive is plugged in it will automatically be added to the pool. AKA build the pool on each boot.

at the moment mhddfs is being build via /etc/fstab

/dev/sdb1 /media/mb1 auto auto,user,rw exec 0 0
/dev/sdc1 /media/mb2 auto auto,user,rw exec 0 0
/dev/sdd1 /media/mb3 auto auto,user,rw exec 0 0
/dev/sde1 /media/mb4 auto auto,user,rw exec 0 0
mhddfs#/media/mb1,/media/mb2,/media/mb3,/media/mb4 /media/master fuse defaults

how can i automate new drives.

---

