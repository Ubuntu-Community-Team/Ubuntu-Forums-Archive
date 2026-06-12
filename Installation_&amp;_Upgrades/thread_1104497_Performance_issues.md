---
title: "Performance issues"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by comradejanus on 2009-03-23
How can I tell if my computer is running at its best when im running ubuntu?

I just made a reinstall of ubuntu, and selected the 177 nvidia driver for my 8300gs card. I also installed the "mod aliases" although I don't know what that does.

Anyway I tested my performance using glxgears and got a frame rate of over 2000 fps.

I'm not running any desktop effects.

The problem is that when I am running a webpage with lots of images on it, e.g. facebook it seems to jitter and struggle when im scrolling through the page. It seems to really struggle when ever theres an image on any window that im scrolling through.

When I look at the same page on my windows partition it seems to scroll through flawlessly.

Also I can get a lot of apps running at the same time with no permformance let downs, leading me to think its something to do with the graphics.

Anyone know what could be causing this? Is there any way that I can test if my hardware is installed properly?

I know its only a minor thing but it really gets annoying after a while. I really love everything about ubuntu and would not want to be put off by this one little let down.

My CPU is amd dual core 5000+ , 2gb of ram (which never more than 25% of which seems to be in use even when I have loads of apps running) and im running 8.10 intrepid.

Thanks.

---

### Post by Chemical Imbalance on 2009-03-23
I have the same card and issue with scrolling in firefox--I believe its a bug in the 177 driver.  I tried Jaunty and it seems fixed with the 180 series drivers.

---

### Post by comradejanus on 2009-03-23
180.11 Sped things up a treat thanks mate.

---

### Post by Chemical Imbalance on 2009-03-23
No problem :)

---

### Post by karlr42 on 2009-03-23
[GLXgears is NOT a benchmark!](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by comradejanus on 2009-03-24
argh, on closer inspection it actually is still happening with the 180.11 drivers...quite a lot on some websites. I've put the live cd back on now and it does'nt happen at all, so im thinking that its definatelly the drivers.

Anyone have any more ideas?

---

