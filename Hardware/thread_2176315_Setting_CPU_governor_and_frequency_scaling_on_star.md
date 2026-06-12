---
title: "Setting CPU governor and frequency scaling on startup"
date: 2013-09-23
forum: Hardware
---

### Post by sberla54 on 2013-09-23
Hello guys,
i've noticed that my CPU used to stay for the 80% of time at the lowest frequency, even if my PC was laggy and with an high load. So, i decided to force the maximum frequency and the "performance" governor.

I've followed this how to: [http://blog.tube42.se/?p=1225](http://blog.tube42.se/?p=1225)

The commands are working correctly. It's a dual core so i have to use:
```
cpufreq-set -f 2501000 -c 0
cpufreq-set -f 2501000 -c 1
cpufreq-set -f 2501000 -c 2
cpufreq-set -f 2501000 -c 3

cpufreq-set -g performance -c 0
cpufreq-set -g performance -c 1
cpufreq-set -g performance -c 2
cpufreq-set -g performance -c 3
```

The problem is that at the next reboot the governor comes back to "ondemand" and the frequency is the lowest.

How can i set governor and frequency on startup?
Can i do it with cpufreq or i have to add those commands on rc.local?

By the way i'm here, are there any risks related to keeping the CPU at max speed?

Thank you.

Regards.

---

### Post by maestrobwh1 on 2013-09-23
I had the same issue on my macbook.  I put the following in /etc/rc.local

```
cpufreq-set -g ondemand
echo 70 > /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
```

echoing 30 will be more responsive, but I notice no lag really at 70 but the frequency monitor stays on the lower end when the laptop is idle.

For some reason, I was locked into 800 mhz until I added the latter line.  I can't imagine the default is 99 or something like that but that is what it seems.

---

### Post by Doug S on 2013-09-24
During starting up your computer will run a script that will sleep for 1 minute and then change the CPU governors from "performance" to "ondemand". See /etc/init.d/ondemand 
You can just make it so that script doesn't run, or comment out the actual change part, or change it to set the governors to performance.

---

### Post by CatKiller on 2013-09-24
You also don't need to run a command for each core; there's an "all related cores" parameter that I don't recall at the moment and can't check.

---

### Post by sberla54 on 2013-09-28
> During starting up your computer will run a script that will sleep for 1 minute and then change the CPU governors from "performance" to "ondemand". See /etc/init.d/ondemand 
You can just make it so that script doesn't run, or comment out the actual change part, or change it to set the governors to performance.

Great tip! Thank you! I will try this!

> 
You also don't need to run a command for each core; there's an "all related cores" parameter that I don't recall at the moment and can't check


Thanks, i think it could be this:
```
cpufreq-set -r -g performance
```

I've tried and this works:
```
cpufreq-set -r -f 2501000
cpufreq-set -r -g performance

```

I've accidentally found Jupiter, a graphical manager for CPU frequency and governor: [http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)
Here's an installation how to: [http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)

Anyway, i think i will stay with the manual mode.

---

### Post by shvahabi on 2014-01-06
> **Doug S said:**
> During starting up your computer will run a script that will sleep for 1 minute and then change the CPU governors from "performance" to "ondemand". See /etc/init.d/ondemand 
You can just make it so that script doesn't run, or comment out the actual change part, or change it to set the governors to performance.

Thanks man, never known of such a trick. You saved my day. Thanks a lot!!!

---

