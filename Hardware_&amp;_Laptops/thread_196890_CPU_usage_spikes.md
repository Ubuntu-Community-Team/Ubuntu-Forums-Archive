---
title: "CPU usage spikes?"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by nickoli_02 on 2006-06-14
I just installed Dapper Drake on my laptop (Gateway 8510GZ) over the weekend and so far I love it. Anyway, I've noticed that the system monitor reports my CPU usage spiking from 0% to anywhere between 30 and 80% for no apparent reason. I've checked out the task manager and the only thing that seems to be eating up a large amount of CPU usage is the system monitor itself (at around 14%...). When it's sitting idle and doing absolutely nothing the spikes aren't very large but even just for playing music and surfing the net and using gaim the CPU usage is consistently over 50%. Anyway, any thoughts are greatly appreciated.

My system specs are Intel Centrino 1.73GHz CPU, ATI Radeon Mobility X700, 100GB HD, 512MB DDR2 RAM, if that helps. 

Nickoli

---

### Post by nickoli_02 on 2006-06-15
no? ok

---

### Post by Onyros on 2006-06-15
Which kernel are you using? There have been a few problems regarding CPU usage with the i686 kernel, there are two possible workarounds:

- Using the i386 kernel instead;
- Refer to this link [http://www.ubuntuforums.org/showthread.php?t=194833](http://www.ubuntuforums.org/showthread.php?t=194833) for the second workaround ;)

Best of luck, mate.

Let us know if you noticed any differences, and what worked (or not) for you ;)

---

### Post by nickoli_02 on 2006-06-15
Wow, huge difference between 686 and 386 kernels! Thanks a lot. What's the main difference between the 686 and 386 kernels anyway?

Nickoli

---

### Post by Onyros on 2006-06-16
686 kernel is optimized for more recent Intel processors (i686 class), whereas i386 is the general, most "basic" and all encompassing kernel :P

Some people with more recent hardware will swear they notice a difference in terms of speed (faster with i686), others (pretty much like myself) will say they notice no differences whatsoever... except in terms of CPU usage ;)

Suppose that's a bug, but I reckon it's already been posted to the Launchpad, as it's pretty common around here with the i686 kernel.

---

