---
title: "Restoring RAID5 array after Ubuntu upgrade"
date: 2009-11-27
forum: Hardware
---

### Post by bobasan on 2009-11-27
Hi all,

I can't get my 4TB RAID 5 array, hardware using Rocketraid controller, to reassemble now that I have upgraded.  I am trying to reassemble the array through

mdadm --assemble /dev/md0 /dev/hdb /dev/hdc /dev/hdd /dev/hde

but mdadm is saything that it can't find a superblock on the /dev/hdb

looking at that array through the Rocketraid bios it shows the array as functional and with no errors so I am at a loss on how to restore the array without data loss.  Any help would be appreciated.

Bob

---

