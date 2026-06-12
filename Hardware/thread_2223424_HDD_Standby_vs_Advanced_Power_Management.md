---
title: "HDD Standby vs Advanced Power Management"
date: 2014-05-11
forum: Hardware
---

### Post by robonelson on 2014-05-11
I switched out an optical drive for a hard drive and I noticed it was killing my battery so I found out I can enable both HDD Standby and Advanced Power Management on the hard drive.

I enabled both, Standby is set at two minutes and APM at level 127 (whatever that means)

My question is, should I just enable one of them at a time or is it okay to leave both on? I noticed that with standby on at two minutes the APM (at level 127) was putting the hard drive to sleep within 10 seconds so it seems like APM is basically overriding the standby timer anyway.

What to do?

Also is any of them better than the other in terms of drive longevity? I see that APM has "downspin" enabled, but I figured standby is basically a downspin too (I mean, it almost shuts it down anyway right?)
So what is the difference? Is one better than the other? Can both work together?


Thanks

---

### Post by tgalati4 on 2014-05-11
APM features depend on the model of the disk drive--which you didn't share.

Hard disks use more power than CD/DVD drives, so yes, you will see a reduction in battery life.  In my testing, laptop drives use 2 to 7 watts of power.  A typical laptop processor will use 15 watts, the screen will use 5 to 10 watts depending on size.  So basically the hard disk is the 3rd largest user of power.  Having 2 of them will drain the battery faster.  

Spindown timers don't save as much as you think because the disk drive's electronics need power all the time and once a disk is spinning, it doesn't use much power to keep it spinning.  Frequent spinups can use more power than keeping a disk spinning--preservation of angular momentum.

If you need more battery life, then get SSD's and a bigger battery pack.

---

