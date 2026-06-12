---
title: "Linux Software RAID 5 changed ownership"
date: 2010-10-26
forum: Hardware
---

### Post by Mwbrouwer on 2010-10-26
I have 4 1TB harddrives running in a RAID5 array. I pulled the power cable from one of the drives to put in another computer. While 1 drive was offline, I figured I'd bootup the system and see how it was doing. It wouldn't mount. 

When I reconnected the 4th drive, the RAID started resyncing on startup. 

I let it resync (for 24 hours) and when I came back, df -h said there was data on the RAID, but I couldn't see any files. Turns out the permissions had changed for some reason. I couldn't find the answer after 30 minutes of searching, so hopefully this will help someone else in the same situation.

chown user /dev/md0
chown user /mnt/raid

:guitar:

---

