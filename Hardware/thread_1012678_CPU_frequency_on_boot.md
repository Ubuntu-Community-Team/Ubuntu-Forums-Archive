---
title: "CPU frequency on boot"
date: 2008-12-16
forum: Hardware
---

### Post by zika on 2008-12-16
I want to set a frequency for all 3 of my cores (AMD Phenom X3 8450) on 2.1GHz.

I've put ```
cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
cpufreq-selector -c 2 -g performance
``` in my /etc/rc.local.

Is there a better way of obtaining that result?

I have CPU frequency scaling monitor (3) on my desktop but they do not store that information.

---

### Post by sdennie on 2008-12-16
That seems like a reasonable way to do it.  You may only need one of the commands though.  It's often the case the the cpu governors of multi-core systems all symlink to the first core so, just setting one core sets them all.

---

### Post by zika on 2008-12-16
no, they are tottaly separate. all 3 are needed. thete is only one problem. in many cases the third command, if left last before "exit 0" in rc.local does not stick. frequency go up and then it falls back. I'll try to put some dummy command ater it to check. no, again, one of them fails back to 1.05GHz. I've tried putting "performance" /sys/devices/system/cpu/cpu...i.../cpufreq/scaling_governor but that did not make a difference. still not solved :)

---

### Post by sdennie on 2008-12-16
If you plan to leave the CPUs at performance (which usually isn't needed), another option would be to remove the powernow daemon (powernowd).  If I'm not mistaken, that will run the CPUs at maximum frequency at all times.

---

### Post by zika on 2008-12-16
> **vor said:**
> If you plan to leave the CPUs at performance (which usually isn't needed), another option would be to remove the powernow daemon (powernowd).  If I'm not mistaken, that will run the CPUs at maximum frequency at all times.

did You mean that 'forcing' performance doesnt' give me more 'power' since it is already available 'on demand'?

by removing powernow You meant uninstalling it or temporarily disabling it? if the answer on my first question is "yes" then this second question is redundant ... :)

I've found in gconf-editor a gnome-power-manager and there is a cpu panel but I do not know the possible options... 

again, if the answer to my first question is "yes" ... ;)

---

### Post by sdennie on 2008-12-16
> **zika said:**
> did You mean that 'forcing' performance doesnt' give me more 'power' since it is already available 'on demand'?

Right.  Modern CPUs can switch frequencies so quickly that a human probably won't noticed the difference between ondemand and performance.  The only reason I can think to run performance is if you are running something like SETI@Home and have it niced.  Niced processes usually don't make the CPU speed jump to maximum so, in this case, you may want to force the governor to performance.

Either way, you might as well test both just to satisfy your curiosity.  Find some benchmarks and test both ondemand and performance.

> 
by removing powernow You meant uninstalling it or temporarily disabling it? if the answer on my first question is "yes" then this second question is redundant ... :)


Either would work actually.  It's probably easiest to just disable it via System->Administration->Services and test what happens though.

---

