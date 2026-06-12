---
title: "Safely update with RAID1"
date: 2008-11-10
forum: General Help
---

### Post by tegel123456789 on 2008-11-10
Hi,

I have Ubuntu server 8.04 and want to update to 8.10.
I have a RAID1 setup where / is mounted on /dev/md1 and /boot is mounted on /dev/md0.
To be on the safe side, I would like to keep my current release on one of the disks in the RAID setup, so I have marked those partitions as faulty and removed them from the MD array. 

If something goes wrong during the release update, can I add the "faulty" partitions on make a sync back to the old release? How do I do that?

Thanks!

BR Anders

---

