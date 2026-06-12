---
title: "building 1 server from snapshot of another"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by whitteng on 2009-05-11
We have two remote Ubuntu 8.04 servers. One is working well (with a 32 bit Ubuntu OS) and we want to get a snapshot of that one and map it onto the other, which is also working, but with a 64 bit OS - we want to move to a 32 bit Ubuntu version. They both have the same hardware. Since they have different IP numbers and the disk partition labels are not going to be the same so we have re-copied the original:

/etc/network/interfaces
/etc/hosts
/etc/fstab
/dev

back over the snapshot. It seems like the newly configured machine may be booting OK, but the network is not coming up properly - maybe an eth identification problem. 

Is there something we are missing - additional files that need to be used from the original system maybe?

Any help would be appreciated.

thanks,
Gary Whitten
whitteng @ con2inc.com

---

