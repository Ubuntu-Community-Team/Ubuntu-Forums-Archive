---
title: "Quick swap questions"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by willix on 2009-08-14
Hy all
I've got a new laptop with 2x300GB hard drives. Will I 'speed' up my system if the root directory (/) and the swap are on different disks (so as to optimize access time)?

Furthemore having 4Gb of RAM, I need at leat the same amount of swap, but will I gain anything if I double it (or at least increase it)? 

Thanks

---

### Post by AmerNewbieInDE on 2009-08-14
yea, ok, i am still a newbie, but what from what i read, swap file is only used IF it runs out of ram.. 4G of ram is alot so most users wont run out. But if you do, yes, it will work better if it is allocated space on a totally differnt drive..

i run my ubuntu on a 320G external sata drive by usb, automatically ubuntu gave itself 8G swap because i also have 4G ram, but it has never seemed to need it.

---

### Post by presence1960 on 2009-08-14
> **AmerNewbieInDE said:**
> yea, ok, i am still a newbie, but what from what i read, swap file is only used IF it runs out of ram.. 4G of ram is alot so most users wont run out. But if you do, yes, it will work better if it is allocated space on a totally differnt drive..

i run my ubuntu on a 320G external sata drive by usb, automatically ubuntu gave itself 8G swap because i also have 4G ram, but it has never seemed to need it.

with 4 GB RAM you won't be using the swap partition but once in a blue moon. Therefore installing it on a different disk is moot. If you want to use suspend/hibernate then you need your swap to be the same size as your RAM.

---

### Post by raymondh on 2009-08-14
Even though we may be talking about differences in 'seconds' ..... at the very least, I would put root and swap on the HD that is set to boot first.  My thinking is that it would be read first.

Swap is dependent on your usage and hibernating needs.  I have 4GB RAM and 1.5GB swap.  It is still possible for hibernation to fail but, in my practice/usage, I rarely get to use total swap and still have not failed to hibernate.   Since you have the space ..... I'd go ahead and experiment with 4GB (or more) swap.  With 600GB total, what's a few GB deducted ;)

Have fun.  Try the liveCD to check how the version plays well with your system and hardware.

Happy Ubuntu-ing.

---

### Post by AmerNewbieInDE on 2009-08-14
wow... i learn something different everyday... seems like everyone has a differnt way of thinking... honestly, thanks for that info, didnt realise linux uses its swap file for also saving suspend info... guess i dont change mine...

---

