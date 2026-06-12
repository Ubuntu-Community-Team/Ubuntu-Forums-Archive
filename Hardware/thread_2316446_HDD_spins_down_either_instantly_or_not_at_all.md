---
title: "HDD spins down either instantly or not at all"
date: 2016-03-08
forum: Hardware
---

### Post by Lockheed on 2016-03-08
I was trying to set some sane spindown time values for my 2.5" Hitach 5k1000 drive but it appears it ignores whatever I set.

The only thing that has an effect it setting APM level with hdparm -B. 
If I set it to 127 or less (which are supposed to be the only levels that support spin down at all), the drive spins down instantly. But when I try to modify it with hdparm -S, it has no effect at all.

Whether I set it to 3 (5 seconds), 30 (2,5 minutes) or even 0 (disables spin down) the drives goes into standby instantly.

The drive is connected to SATA III interface in ThinkPad t420s. TLP was disabled for the purpose of testing values with hdparm.

---

