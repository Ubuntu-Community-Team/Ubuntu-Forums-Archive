---
title: "CPU Running Below Capacity?"
date: 2013-12-27
forum: Hardware
---

### Post by bshatt1987 on 2013-12-27
Hi, I've used Lubuntu for a while, since I've got an older laptop.  It's a Gateway MX7515 with a Mobile AMD Athlon 64 Processor 4000+
Anyway, when I start up the computer and open the System Profiler and Benchmark, it shows that the processor is running at 2.6GHz, but after a couple minutes it shows that it's running at 800MHz.
That seems exceedingly slow compared to what it shows upon startup.
I'm wondering if there's anything I can do to make it work faster?
I'm pretty much a Linux noob, so whatever you tell me try to put it in laymen's terms, please.

---

### Post by mikewhatever on 2013-12-28
Usually, CPUs scale down their frequencies when idle or not under load to save power and reduce heat and fan noise. It's a useful feature, but if you wich to scale yours up, try installing the **indicator-cpufreq** package. Here's [how it works]("http://askubuntu.com/questions/142688/cpu-frequency-scaling-for-12-04").

---

### Post by bshatt1987 on 2013-12-28
Okay, I'll give that a shot, thanks.

---

