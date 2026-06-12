---
title: "New kernel breaks suspend on thinkpad T60"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by stbaker on 2006-08-06
Hey everyone,

I own a thinkpad T60 with the core duo 1.83 GHz processor. I've been using the 2.6.15-23 kernel for a while, because the 2.6.15-26 kernel was pretty slow on my system, even with the fglrx drivers running. However, when they added an update to the 2.6.15-26 kernel (they moved from 26-45 to 26-46, i think), it seemed to work well on my system. It also seemed to add some battery life. However, suspend stopped working. It was working fine with the 2.6.15-23 kernel. I'd really like to use the newest kernel, as it seems to extend my battery life, but its not that useful without being able to suspend. Any thoughts?

Thanks,

Sean

---

### Post by shizow on 2006-08-09
i think i have the same problem with my T43, since some recent update, my suspend does not work anymore, maybe it is really the latest kernel update from 26-45 to 26-46?

Update:
it seems that my problem is the fglrx 8.27.10 drivers, when using the radeon ati drivers, my suspend works
any suggestions?

---

### Post by arijarot on 2006-09-07
i don't know what your kernel is, im no expert, but from what i read you should be using the 686 kernel with the duo.

---

