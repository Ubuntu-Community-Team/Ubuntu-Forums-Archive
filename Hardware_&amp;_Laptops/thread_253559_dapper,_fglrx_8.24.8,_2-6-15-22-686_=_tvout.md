---
title: "dapper, fglrx 8.24.8, 2-6-15-22-686 = tvout?"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by lir on 2006-09-08
I was trying to be concise as much as I can with the topic.
The current version of fglrx I have is:
```

ii  xorg-driver-fglrx      6.9.0-8.24.8+2.6.15.9- Video driver for ATI graphics accelerators

```

Any chance my SVideo TV-OUT is supported with this version?
If it helps, it's an Acer 5562WXMi laptop.


Thanks.

---

### Post by pixelmoon on 2006-09-12
I see a lot of poeple trying to edit their xorg.conf files to get dual monitors or tv out.  If you have fglrx installed correctly then all you need to know is **aticonfig --help**.

For when I had fglrx installed on my ati radeon 9700 on my laptop this is what I did.

**aticonfig --help**
(look at the tv section)
**aticonfig --enable-monitor=lvds,tv**
(this should make a clone on the tv out but I found that it only displayed in black and white.  I had to change the tv format to NTSC-M)
**sudo aticonfig --tv-f=NTSC-M**

That should get you to have it cloned at least.
If you want to get it as dual head, you can follow the example in the --help page.  I think it goes something like this:

**aticonfig --initial=dualhead --screen-layout=left**

I think...it's all in the --help section anyway.  Hope that works out for you!

---

