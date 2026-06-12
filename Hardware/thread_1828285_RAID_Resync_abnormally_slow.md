---
title: "RAID Resync abnormally slow"
date: 2011-08-18
forum: Hardware
---

### Post by tylersontag on 2011-08-18
Alright, i just had a RAID crash on me (long story, it involved zeroed superblocks and bad recovery's resynching trash data)  and i finally gave up reconstructing it and just decided to start over.

I zeroed out all three drives (this was/is a RAID5 with 3 drives) and removed the partition off of them.  Using Disk Utility i then created a new LV from the tree drives.  It comes up degraded and begins to resynch... everything normal right?

then i notice how long its taking, i do a cat /proc/mdstat and this is what i'm staring at

```
recovery =  1.3% (27151372/1953511424) finish=81327.2min speed=394K/sec
```

Rediculous.  My RAID card is a RocketRAID 1740, there is no reason for 0.4 MB/s synch speeds.   SOmething has to be wrong here.  Any ideas?

---

