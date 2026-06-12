---
title: "Help! High cpu usage when playing/streaming video."
date: 2010-10-17
forum: Hardware
---

### Post by jaaR on 2010-10-17
I am running Ubuntu 10.04 32 bit DE and loving the experience but...

**System info:** Dell xps m1330
             Core 2 duo 2.2 Ghz
             2 GB RAM
             Intel Corporation Mobile GM965/GL960 Integrated Graphics
             Controller (rev 0c)

**Problem:** Streaming video increases cpu usage to 60-70%. In processes I noted Xorg at the top. I previously had windows vista installed with this (R141246.exe) driver installed and cpu usage was way lower performing the same task. 

I think the driver is the issue, if I'm correct is there a fix? If the driver isn't the issue please point me in the right direction.

Thanks a lot for any help.

---

### Post by TBABill on 2010-10-17
High CPU in Firefox or Chromium? Mine is about 39% on Chromium but I'm on 64 bit. Can you try both browsers and see if it's the same? That would help narrow it down.

---

### Post by TBABill on 2010-10-17
You're using Jaunty? Do you have the latest adobe flash installed instead of gnash?

---

### Post by lovinglinux on 2010-10-17
Is probably the graphics driver. I have a Core2 Duo too and flash video eats 25%-40% of CPU.

Also make sure you have the Adobe flash plugin, since the alternatives could use more CPU.

---

### Post by jaaR on 2010-10-18
Thanks for the info guys. 
Yes I've got the latest flash plugins and it's the same on both chrome and firefox and opera. I really think that it's the driver not being used optimally. I've done a lot of searching online but have not come across any fix. Is there a way to load a an .exe video driver on ubuntu.

Any additional info is welcomed.

---

### Post by lovinglinux on 2010-10-18
> **jaaR said:**
> Thanks for the info guys. 
Yes I've got the latest flash plugins and it's the same on both chrome and firefox and opera. I really think that it's the driver not being used optimally. I've done a lot of searching online but have not come across any fix. Is there a way to load a an .exe video driver on ubuntu.

Any additional info is welcomed.

See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by krtica on 2010-10-18
Well, I have similar configuration and I'm using Ubuntu on it for more than 2 years now, I think.
Intel Core 2 Duo T5270, 4GB memory, Intel GM965/GL960.
I always had processor(s) usage ~50% with peaks up to 60% when watching videos on YouTube. And on flash games, - even more.
But I never considered it as a problem. :O
I think it's just about Flash, as not quite happy advent. :D
I have dual boot on my comp. and it's processor consuming process in Windows too.
I'm not sure there is some solution. But if I'm wrong, I would also be thankful for it. :)

PS: I tried many 'optimizations' and 'googleing' for a while, when I noticed it for the first time. But nothing really helped.

---

### Post by TBABill on 2010-10-18
Lovinglinux's Flash Aid solved all my problems. Now it's standard for me to install it after I get my system up and running. I run 64 bit and ubuntu-restricted-extras installs 32 bit flash. But Flash Aid takes care of swapping out the 32 for the 64 bit and the system handles videos much better now.
 
Thanks lovinglinux!

---

### Post by lovinglinux on 2010-10-18
> **TBABill said:**
> Lovinglinux's Flash Aid solved all my problems. Now it's standard for me to install it after I get my system up and running. I run 64 bit and ubuntu-restricted-extras installs 32 bit flash. But Flash Aid takes care of swapping out the 32 for the 64 bit and the system handles videos much better now.
 
Thanks lovinglinux!

You are welcome.

---

### Post by jaaR on 2010-10-18
**Thank u Lovinglinux**, Flash Optimization helped a lot, I've noted a remarkable decrease in cpu usage when streaming (just got of youtube watching ronaldinho get on this weekend Ole!). 

Thanks LL again for the link and thanks to all who contributed to this thread. God bless u guys.

---

### Post by lovinglinux on 2010-10-18
> **jaaR said:**
> **Thank u Lovinglinux**, Flash Optimization helped a lot, I've noted a remarkable decrease in cpu usage when streaming (just got of youtube watching ronaldinho get on this weekend Ole!). 

Thanks LL again for the link and thanks to all who contributed to this thread. God bless u guys.

You are welcome.

---

### Post by krtica on 2010-10-19
I'm really interested in this subject. But for the Flash in general, for example Flash games. (Like those on Facebook.)
I tried many things, but my proc. is always >45% and 60°C when I'm using Flash. Finally I quit testings and resigned.

I tried this also, lovinglinux, but I didn't notice any change. (But I never had a problems with video.)
Is there any way to speed up Flash in general? Any recommendation?

[I]PS: I already found your blog before, while I was searching for Firefox optimization.
**Thank you for your efforts.**[/I]

---

