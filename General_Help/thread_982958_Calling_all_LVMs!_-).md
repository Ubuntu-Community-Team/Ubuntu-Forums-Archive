---
title: "Calling all LVMs! :-)"
date: 2008-11-15
forum: General Help
---

### Post by Th3Professor on 2008-11-15
...like the old tv show, "Calling all cars!" (Dragnet)...

Anyway, I'm looking for some feedback on LVM for my new set-up.

I recently built a computer (4 hard drives (4x500GB)) and set it up so drive #1 consists of operating systems, base apps, and temp work (on music recording for example) and drive #s 2, 3, 4 are using RAID5 via mdadm.

The RAID5 group has a 128 chunk-size, fs type is ext3 set-up with -b 4096 and stride=32 (to match performance with the chunk-size). Now on to the LVM...

pvcreate /dev/md0
vgcreate -s 32M lvm-raid /dev/md0 (32M for RAID5's 931GB)
vgdisplay lvm-raid (to get number of PEs available for volume creation)
lvcreate -l 29808 lvm-raid -n lvm0
lvdisplay /dev/lvm-raid/lvm0
mke2fs -t ext3 -b 4096 -E stride=32 /dev/lvm-raid/lvm0
mount /dev/lvm-raid/lvm0 /mnt/
df -h /mnt/ (and it shows 917GB size, 200MB used, 871GB available)

Why is it not showing 931GB for the size (as it is after setting up RAID5)?

Is it because I created ext3 two times? (Should I only create ext3 one time (after creating lvm0?))

How would I put this into fstab?

The parts within vm0 that I'd like to create are:
/studio/vault
/zone (for Solaris /zone/home - though I'm not sure if this will work with Solaris)
/home (for my "other linux" install)
1 additional linux swap and 1 additional unix swap

I'm not sure if I can do this but would like to - set up the LVM so I can access /studio/vault without having to go to something like /lvm-raid or /lvm0 first. The trick is, I'm not sure how.

I'm doing this now so that I can redo it all, hopefully correctly, before I start using/storing/etc. ;)

UPDATE:
I created this thread in a silly way, not letting people know there are questions enclosed... unless someone knows how I can set my vm0 directories to be accessed without an /lvm-raid or /lvm preceding, then you can ignore this thread. Thank you. :)

---

