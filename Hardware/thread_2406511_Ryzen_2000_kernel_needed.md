---
title: "Ryzen 2000 kernel needed?"
date: 2018-11-21
forum: Hardware
---

### Post by zephar123 on 2018-11-21
Ubuntu 18.04
So I got on order a 2600x Processor. I was wondering if the kernel 4.15  is enough or are their reasons to install a newer version of the kernel.  (example 4.15 does not fully support the processor.)

I figure some other people have probably already messed with this so  figured I would ask. I know the 1000s series of Ryzen fully worked with  4.15, but 2000s series is different =). So thanks in advance to any  information you can share.

---

### Post by stebomurkn420 on 2018-11-21
I have the Ryzen 2700x and Ubuntu 18.04 is running perfectly. Took my compiling times down to 75 minutes clean building from 4 hours with my i5-7600. Great bargain CPU! All 16 threads show 98%-100% use while compiling... (building android).

---

### Post by kurt18947 on 2018-11-22
The 2600X does not have integrated graphics does it? If not you should be fine. I recently upgraded a 9 year old system with a Ryzen 3 2200G and the integrated graphics adapter didn't work. I knew there was the possibility of a problem so reinstalled a few years old AMD graphics adapter and all is well. I think the Vega graphics require kernel 4.18 and a new version of Mesa or something like that.

---

### Post by zephar123 on 2018-11-22
> **kurt18947 said:**
> The 2600X does not have integrated graphics does it? If not you should be fine. I recently upgraded a 9 year old system with a Ryzen 3 2200G and the integrated graphics adapter didn't work. I knew there was the possibility of a problem so reinstalled a few years old AMD graphics adapter and all is well. I think the Vega graphics require kernel 4.18 and a new version of Mesa or something like that.

Yep thats where i was getting confused was with some of the 2400gs I have done for other people. Yep 2600x (raven ridge) appears to be fully compatible with kernel 4.15

thanks gusys

---

