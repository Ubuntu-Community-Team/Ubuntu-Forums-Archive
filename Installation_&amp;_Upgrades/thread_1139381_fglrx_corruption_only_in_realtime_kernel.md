---
title: "fglrx corruption only in realtime kernel?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by chyldofthebeat on 2009-04-27
Oi! I've run into an interesting reaction when trying out the realtime kernel (I'll be more specific now).

I have an ATI Radeon 3650 and the fglrx 8.600 driver, running Jaunty (upgraded from Intrepid). I have two kernels I am using on my system (and the headers for each)... 2.6.28-11, and a realtime kernel, 2.6.28-3-rt. I also have some older ones compiled, like 2.6.27-13, but I'm not using them right now. 

Anyway, the non-realtime kernel works perfectly fine, but when I run the realtime kernel, I get a corrupted screen when GDM loads.  Originally I think DKMS was failing to build the driver, but I read that I needed the kernel headers, and I have those now. DKMS seems to build the driver fine (it says OK on bootup). 


I realize this probably isn't enough detail, so let me know what file contents I should post. Thanks!


Ryan

---

