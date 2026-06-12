---
title: "cpufreq puts CPU in lowest mode under heavy load"
date: 2008-05-11
forum: Hardware
---

### Post by theophile on 2008-05-11
I have a Dell Inspirion 1501 with a 2 ghz AMD processor. It supports CPU frequency scaling. However, when the machine is performing cpu-intensive functions (compiling kernel, etc.), when the governor is set for "performance," the speed scales down to the lowest speed, 800 mhz (40%). Once the compiling is complete, it goes back to the full 2 ghz.

This is extremely annoying and counter-productive. It did this with the 2.6.22-9 kernel in Gutsy and it's still going it with the 2.6.24-16 now that I've upgraded to Hardy. Is there any way to fix this behavior? 

Thanks!

---

### Post by stream303 on 2008-05-12
I'm trying to find out why powernowd doesn't seem to do anything on my box with Hardy, so I uninstalled it, and installed CPUDYN instead.  Scaling now works, although I'd like to find out why powernowd doesn't work.

Maybe try cpudyn instead of powernowd for a temporary fix....

---

### Post by theophile on 2008-05-24
I still need to figure out what's going on here. I tried ripping a DVD with HandBrake (awesome app) the other day and the processor slowed down to 800 mhz for the entire process. Something isn't right here!

---

### Post by jpkotta on 2008-05-26
It's the new CPU scheduler in the kernel.  They (Ubuntu) misconfigured it.  A better kernel will get pushed out as an update soon.  You can get the new kernel immediately if you add hardy-proposed to your /etc/apt/sources.list and install the latest kernel.

[QUOTE=/etc/apt/sources.list]
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) hardy-proposed main restricted
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) hardy-proposed main restricted
[/QUOTE]
(use your own favorite mirror or archive.ubuntu.com)

```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install linux-generic
```

You can also tweak the values in /sys/kernel/uid/$UID/cpu_share to get more CPU time for your user.

---

