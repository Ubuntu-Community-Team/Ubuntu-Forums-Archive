---
title: "ext3 Format an external HDD very slow"
date: 2009-10-12
forum: Hardware
---

### Post by Squash101 on 2009-10-12
I am using GParted on Ubuntu 9.04 to format an external 320G USB2 hard drive to the ext3 file system. So far it has taken a really long time (more than 5 hours) and there is no progress indicator.

Is this normal? Should I cancel? My research shows that people who have cancelled have created lots of other problems.

Your experience would be appreciated!

---

### Post by Dark_Stang on 2009-10-12
Ext3 usually formats pretty quickly. As long as you aren't trying to convert an old filesystem to a new one while maintaining data, I'd just cancel it and try again. It is possible that the drive is failing though, which would cause it to take forever. But the partitioner is probably just locked up.

---

### Post by dabl on 2009-10-12
> **Squash101 said:**
> 

Is this normal?



No.

> 

Should I cancel?



Yes.

Something obviously went way wrong there, and there's no guarantee that anything is going to work, but I don't imagine it should take more than 20 minutes to format a 320G USB drive.

Cancel it and try again, and unless you're planning to use it on kernels older than 2.6.28, you might as well choose ext4 -- the fscks are way faster on ext4.

If the drive is borked (i.e. you can't format it with anything), then you can try to "dd" it back to life.  That can be explained in another post, if necessary.

BTW, that drive needs to be _un_mounted for partitioning and formatting, in case you didn't know.

---

### Post by Squash101 on 2009-10-12
Never mind! It finished formatting about 10 hours after starting.
320 Gig HD on USB2 = 10 hours.

I'm guessing that the drive is ready for the trashbin.

Just for fun, I'll try it again as ext4.

Thanks for the quick replies!

---

