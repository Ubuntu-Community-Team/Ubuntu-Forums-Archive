---
title: "Optimizing RAID5 (MD)"
date: 2014-06-09
forum: Hardware
---

### Post by AntiMattR on 2014-06-09
Hi all.

I've built a new NAS system with 4 drives in RAID 5 (mdadm) configuration.  I would like to tune MD so that the bottleneck is either the drives or the link between the NAS and the devices using it.  Since the entire role of the machine is to serve data from this drive array I want MD to use all of the cores and all of the RAM it needs to perform.

I've found a few tuning scripts (like the one below) but a lot of debate over them.

[http://ubuntuforums.org/showthread.php?p=11646960]("http://ubuntuforums.org/showthread.php?p=11646960")

If anyone has suggestions please let me know.  Thanks

---

