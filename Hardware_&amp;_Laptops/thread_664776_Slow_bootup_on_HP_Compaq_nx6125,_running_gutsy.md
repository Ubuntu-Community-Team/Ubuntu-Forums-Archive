---
title: "Slow bootup on HP Compaq nx6125, running gutsy"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by Robin-o on 2008-01-11
I have been running Gutsy for about a month now and I think its awesome-everything apart from the fingerprint reader worked straight out the box!  However, even though Im running it with about 600mgs of RAM its seriously slow on the boot time-about 4mins. Anybody got any ideas? Here I my specs of it helps:


Model: HP Compaq nx6125
Processor: Mobile AMD Sempron 3100+
Wireless Card: Broadcom 4318
Graphics Card: None
Gutsy: 7.10

---

### Post by iamkrazee on 2008-06-12
> **Robin-o said:**
> I have been running Gutsy for about a month now and I think its awesome-everything apart from the fingerprint reader worked straight out the box!  However, even though Im running it with about 600mgs of RAM its seriously slow on the boot time-about 4mins. Anybody got any ideas? Here I my specs of it helps:


Model: HP Compaq nx6125
Processor: Mobile AMD Sempron 3100+
Wireless Card: Broadcom 4318
Graphics Card: None
Gutsy: 7.10

Your answer is probably hidden somewhere in /etc/init.d. Figure out for yourself! And by the way, 6125 with sempron.. are you sure??

Also, if you're correct about the model, nx6125 that is, then I'm pretty sure it ships with Xpress 200M which requires. You will require fglrx for that. Enable proprietary drivers. 

And most importantly.. Consider upgrade to Hardy. Works like a splendor here.

---

