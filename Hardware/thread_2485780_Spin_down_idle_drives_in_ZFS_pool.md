---
title: "Spin down idle drives in ZFS pool?"
date: 2023-04-09
forum: Hardware
---

### Post by papriak on 2023-04-09
I would like to save some power and heat-generation when my server is idle.

The system uses a SSD for the OS, but the hosted network storage uses traditional spinning drives in RAIDz2.

Is it safe, or even recommended, to let those drives spin down after a period of inactivity?

---

### Post by #&amp;thj^% on 2023-04-09
With only a few drives and only spinning down half day... I wouldn't as it's not worth the additional likelihood of failure, wearing out faster, etc...

Say you have 5 spun down for 10hrs a day... so they use 5*4w @ idle (estimate) = 20w * 10hrs = 200w saving per-day and * 30 = 6000 watts or 6kWh and then * that by your power cost per kW for me that is 25 cents now. $1.5/mo saving or $18/year. It would take 10+ years to 'pay' for a drive with the savings from power so ymmv with value of that vs. causing a failure... 
For loads of folks at home, the power savings are simply too small to be worthwhile. 
```
zpool status
  pool: bpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  4e4e33f0-99ba-1a45-93ae-b1bdbd6173d5  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   ONLINE       0     0     0
	  81d5c60e-235e-7043-a410-b2c9dbb5c064  ONLINE       0     0     0

errors: No known data errors

```

---

### Post by papriak on 2023-04-09
Thanks for your response, it was a great argument against pursuing monetary savings.

But what about the fact that my room gets so much warmer while the server is running?  The drives seem to be the warmest components even with fans on the cages.

---

### Post by #&amp;thj^% on 2023-04-09
I'll leave that one for you to decide,
I've just recently built a Air cooled Tent with a duct leading out side, seems to suit my needs.

---

