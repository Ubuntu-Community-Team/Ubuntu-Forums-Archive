---
title: "ATI Drivers and Google Earth"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by ctukel on 2006-11-10
I have installed Ubuntu on HP zt3000 laptop with ATI Mobility 9200 Video card.
I tried to install ATI drivers (fglrx) and finally I got them working. But when I restarted computer, the screen was black with some random pixels. 
From the forum discussion, what I noticed that it is a Modeline problem.
So I set the modline in monitor section in xorg.conf. 
Now I noticed, that Google Earth stops at "Initializating.." and does not respond at all.
Another "Stellarium" did not work. When I start it, again I get a messy screen. 
My monitor has 1920x1200 resolution, and I don't know how to get exact specs. (I can't find in the manual)

Is there any way to run these application while having ATI driver is already installed?

I will really appreciate your help.

Caglar

---

### Post by cogenthack on 2006-11-14
I'm having a similar problem, I'm sure it worked in 6.06 but hasn't since the upgrade. If I find a solution, I'll get back

---

### Post by ctukel on 2006-11-15
I removed fglrx drivers and switched back to original configuration. Now it seems both programs work perfectly. 
I wanted to run Beryl but it constantly crashed on certain programs and even screen savers. Besides, I had shut down/start up problems, so it turned out to be Beryl is not suitable for my machine.

Let me know if still have a work around on this issue.

Thanks.

Caglar

---

### Post by con on 2006-11-16
This guy seems to have a solution
[http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/683541/page/vc/vc/1](http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/683541/page/vc/vc/1)

---

