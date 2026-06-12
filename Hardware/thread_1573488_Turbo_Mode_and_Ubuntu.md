---
title: "Turbo Mode and Ubuntu"
date: 2010-09-12
forum: Hardware
---

### Post by mrmylanman on 2010-09-12
Hi all,

I have an Intel Xeon L3426 processor in my desktop that I picked up super cheap, and figured at 45W it's very hard to go wrong.

Essentially, it's the same thing as a laptop Core i7, except in an LGA1156 form factor.  It runs natively at 1.86GHz, however with Turbo Mode it is able to go up to 3.2GHz in single-threaded situations.  I was trying to verify if this is the case, since I hear Linux 2.6.33 and up should theoretically support it, and 10.10 is at 2.6.35 according to the System Monitor.

Speed Step works properly (it normally idles at 1.2GHz and then jumps up to 1.87 at load).  The stock governor is in use, which I believe is ondemand.

To test whether or not Turbo Mode is working, I ran one instance of cpuburn and ran "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" while cpuburn was still running in another terminal window to check which frequency the CPU is running at.  It returned:

1200000
1200000
1200000
1200000
1868000
1200000
1868000
1200000

Now since technically 2 cores are loaded, maybe that is why, although it is supposed to still ramp up to 2.93GHz in that case.

I do know that it doesn't appear lm-sensors is able to detect any thermal sensors except my video card, so is that possibly a reason?

Anyway, hope someone knows what's going on!

---

### Post by mrmylanman on 2010-09-13
Anyone have the lowdown on turbo mode and Ubuntu?

---

