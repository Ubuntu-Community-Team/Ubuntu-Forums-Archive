---
title: "mdadm raid5 rebuild times"
date: 2017-11-01
forum: Hardware
---

### Post by shoeleshunter78 on 2017-11-01
I am about to build a Raid5 mdadm array on 3X 4TB discs. The run at 7200rpm

Before I do that, I am wondering what the ballpark rebuild time is for an array like that if one 4TB drive fails. Since this workstation needs regular down time, this could effect my decision to go this way.

---

### Post by TheFu on 2017-11-02
RAID on large drives is NOT advised.  How fast a rebuild will happen is dependent on the controller, disks, workload.  A 4TB disk without RAID took over 26 hrs to restore from a backup.  A non-busy RAID, I would expect 3x that long.  A storage vendor was testing a rebuild using 4TB drives and it was over 35 days when he killed the test.

The current recommendation from RAID/storage vendors is to use enterprise SSDs for RAID devices, not spinning disks. There is a conference talk from SELF 2017 about just that. Hopefully you can find the video.

RAID solves 2 issues - HA and read performance.  Nothing else.

---

