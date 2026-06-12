---
title: "amount of user memory"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-04-11
In my brand new installation of Hoary, with no tweaks, additional software whatsoever, i typically have between 130 and 160 mb of user ram available out of 512 mb on my 1.8 ghz p4m laptop. in windows xp with sp2 i'd typically have more than half of it available.

i'm not well informed on linux memory management, so can anyone enlighten me on if this situation is normal for Hoary? many services are running in the background, and almost every one of them takes more than 20 mb, but they're all in "sleeping" state; do they not consume actual ram in that state? (pardon the very newbie tone on these questions ;) ) 

my rough observation is that apps in Hoary take longer to launch and access swap space much more than their windows counterparts. i know i'm talking about two different worlds with two different sets of rules, but i feel Hoary's performance is suffering from a critical bottleneck in my system, and having observed the amount of user ram available has risen my suspicion. 

thanks!

---

### Post by az on 2005-04-11
Linux will use as much ram as it can to gain performance.  It will drop cached memory if it can before swapping.  You can still get great performance on a small 128 meg system.  I have a system with 96 megs and I rarely swap.

On all of the systems that I have tried both, Ubuntu is either as fast, or faster than Windows.

I guess it depends on your hardware.  I run on pretty low-end stuff.

---

### Post by 23meg on 2005-04-11
what swap size is generally recommended for a configuration like mine?

---

