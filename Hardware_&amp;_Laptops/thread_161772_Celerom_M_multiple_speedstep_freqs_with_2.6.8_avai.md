---
title: "Celerom M: multiple speedstep freqs with 2.6.8 availlable, just two freqs in dapper"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by Netwalker on 2006-04-17
I have a Celerom M 2.5GHz Toshiba Satellite A10 laptop. I installed Ubuntu on it and keep it more or less updated since 4.04 was released. I have just upgraded to dapper yesterday, and -appart from some cool and unexpedted upgrades, like full out-of-the-box synaptics touchpad support- I have found a quite strange problem.

You see, With the default kernel that hoary shipped, I could load some kernel modules and get full speedstep support. To be more precise, speedstep-lib and p4-clockmod modules. I had like eight different CPU frequencies to choose from, which was great: 15 minutes of unreal tournament at full CPU freq (2.5GHz) means CPU heat pumping up to 82ºC!
With this option, I could set CPU freq to, say, 1.25GHz and still be able to play games or something like that with CPU heat arround 55ºC.

The problem is, I have upgraded to dapper default kernel, and all my full range of freqs to select from has just been reduced to 2.5GHz or 2.1875GHz.
Totally unacepptable, taking into account I still use this machine for (classic) gaming (Q3A isn't death yet... :P ). 

Does anyone knows how can I get back all the supported freqs of my 2.5GHz pentium Celerom M with my 2.6.15-20 kernel? And don't tell me the CPU doesn't support if, I positivelly know it can do what I ask for. It has been doing it for two years now.

---

### Post by bboozzoo on 2006-04-24
got the same problem, before update to 2.6.15-20 I could change frequencies from 300MHz up to 2.4GHz with 300MHz step, now only 2.4 and 2.1 are available, possibly the last kernel upgrade broke cpu frequency scaling

---

### Post by Tom Tiger on 2006-04-26
Or the module is missing?  I'm still running 2.6.12 on my Sat Pro A10.  No problems here, but I must admit I haven't really looked into it, it worked straight out of the box (5.10) and except for upgrading the kernel to 2.6.12 I686 I haven't done much to it (well the usual upgrades)  but I only watch movies on it :)

---

### Post by adam.tropics on 2006-05-09
Try to start *p4-clockmod*, *cpufreq-ondemand*, and *cpufreq-userspace* modules. It works on my celeron m. Then install cpufrequtils, which just makes altering settings a bit simpler, and run the gnome applet, and see how it goes.

---

### Post by macgabhs on 2006-05-29
I was having the same issue after upgrading to Dapper from Breezy. I'm running a sony vaio with an intel pentium M 1.76GHz chip. I found the solution to be removing powernowd via synaptic then reinstalling it and rebooting. Not sure if this will work with a celeron M but it might

---

### Post by ariel on 2006-06-02
I'm having a similar problem with my x60s. Only three choices, draining the battery too fast. I'd like to machine to throtle more (smallest freq is 1G, I'd like 600Mhz). It appears that the CPUs can handle 8 speeds, but only 3 of them are reported by cpufreq-info. Any ideas anyone?

Thanks

---

