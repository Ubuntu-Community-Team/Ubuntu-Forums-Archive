---
title: "Centrino and 686-kernel: Slower performance, no cpu scaling, higher temperature"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by Wermut on 2006-06-17
For me the kernel optimized for the 686 processors has the following effects:

-- Drastically reduces performance
-- No scaling of the cpu frequence occurs
-- Temperature of the cpu is ~20° higher

I did not have this experience with Breezy.
(My notebook is a Samsung X20 with a 1700 Mhz Centrino processor.)

Has somebody observed the same effects?

---

### Post by blimpyboy on 2006-06-17
I have a Pentium M 760 (2Ghz) and cpu scaling isn't working for me either with the 686 kernel.  I haven't tried the 386 kernel.  powernod is running.

686 kernel worked fine with breezy.

---

### Post by nolongerlivecd on 2006-06-17
Using 686-kernel. 2GHz. Doesn't work either. cat /proc/cpuinfo still works out to be 1995MHz

---

### Post by Wermut on 2006-06-18
Is this a known issue? If not it should be brought to the attention of the maintainers.

I find it quite annoying, since notebook support was literally *perfect* for me in Breezy and it is a shame that the LTS edition falls back in this aspect.

---

### Post by ysse on 2006-06-18
Wermut,

I did a little bit of checking up on my system. 

One one hand, it is as nolongerlivecd says, /proc/cpuinfo always shows full frequency with the 686 kernel, but shows different CPU frequencies when booted with 386.

On the other hand, the panel applet "CPU Frequency Scaling Monitor" does show that scaling is taking place also when running 686, as does cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq (600000 at lowest, corresponding to 600 MHz).

My kernel is 2.6.15-25-686, on a 2 GHz. I basically did a fresh install of Dapper, only kept /home from Breezy.

Any particular applications that are slower, and by how much?

---

### Post by Wermut on 2006-06-18
The scaling issue seems to be a  known issue and a fix has already been committed: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014)

As for the slower applications: basic operations take several seconds (e.g. the animation when you click an icon in Konqueror).

---

