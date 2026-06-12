---
title: "Why does Ubuntu allow 1 cpu to run at 100% and the rest at 10% or less ?"
date: 2015-01-12
forum: Hardware
---

### Post by vincej on 2015-01-12
Hi - I have a lot of Google Chrome tabs open ... maybe 20 or so. I need them all - I'm a software developer. 

Plus I have other apps operating, but nothing heavy, all text based dev tools etc. 

I have a dell desktop (8300) with with a AMD 6700 GPU, a 2nd Gen i7 CPU with 16GB RAM and a 250 GB SSD and 2 TB of HDD. 

My CPU  has 8 cores. CPU #8 runs at 100% all the time, whilst the other CPU's run at less than 10%. 

When I look into the processes I can see that 19 of the 20 Chrome processes are taking 0% of the CPU but 1 chrome process of the 20 takes 96%. 

If I should open an additional tab, I notice that Ubuntu passes the Chrome process off the CPU #4 which then also runs at 100%. Another tab and Ubuntu sends it back to #8 and so, back and forth it will ping pong. 

So, what gives ?? I had believed that Ubuntu smoothed the CPU usage across the available cores as in symmetrical multi-processing sharing the load across the total available processors ... no ?? 

Is there anything I can do to smooth the load between the processors ?? 

Many thanks !

---

### Post by JustinBongard on 2015-01-12
You could disable the hyper threading in the BIOS.  That will bring you back down to 4 cores.  I've done it before with no problems.

---

### Post by vincej on 2015-01-12
will that smooth out the cpu usage ?

---

### Post by Yellow Pasque on 2015-01-12
Someone just wrote about this problem a couple days ago. It turned out to be this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1386473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1386473)

---

