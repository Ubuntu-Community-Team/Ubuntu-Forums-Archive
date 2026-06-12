---
title: "Cpu scaling: cpufreq_perfomance module missing"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by phenest on 2007-07-15
My laptop defaults the cpu scaling governor to ondemand. I would like to have it default to performance on boot instead. I can use the toolbar applets CPU Frequency Scaling Monitor to set the performance governor. I changed the settings in the Configuration Editor to use the performance governor but it still defaults to ondemand. If I type sudo modprobe cpufreq_performance in a terminal, it says the module wasn't found. So this must be the problem. So where do I get this module from?

---

### Post by 5-HT on 2007-07-15
The performance governor is usually compiled directly into the kernel (haven't checked latest .configs). What about setting the governor in /etc/rc.local? Something like the following, edited according to your cpu value, would do it: cpufreq-set -c 0 -g performance
If ondemand is still taking over, a dirty little hack would be to blacklist it and see if conservative gets free reign then (worked for me).
cheers,

---

### Post by phenest on 2007-07-15
cpufreq-set -c 0 -g performance will not work because the cpufreq_performance module does not exist.

---

### Post by 5-HT on 2007-07-16
> **phenest said:**
> cpufreq-set -c 0 -g performance will not work because the cpufreq_performance module does not exist.

Have you tried it? cpufreq-set does not require that the governors be compiled as modules; it works just fine if they're compiled directly into the kernel (which is what I was hinting at earlier:If the performance governor is compiled directly into the kernel there will be no module, and no need for a module.). Have you tried blacklisting ondemand? 

From your original post it looks like you can use the performance governor if you switch over to it manually with the applet (if so, you do have the governor). Just to make sure, what are the available governors?
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 

```

---

### Post by phenest on 2007-07-16
Yes, I have tried it. I gives an error. Performance is listed as an available governor, but cpufreq-set gives an error when I try to set it. And performance is listed as being available. I will try to blacklist ondemand and check the results.

---

### Post by phenest on 2007-07-16
I have just turned my laptop on to discover the cpu running in performance mode. Weird! I haven't changed anything so I'm going to leave it and see if it continues to use it.

I don't know if it's a coincidence, but I turned to using the -386 kernel instead of the -generic kernel. That's probably it. I changed the kernel to solve general performance problems which the SMP in the -generic kernel was causing.

---

### Post by phenest on 2007-07-17
I've found the problem.

Let this be a lesson to everyone: Check your speling, um, I mean spelling.

In the Configuration Editor, I had typed "performance" for battery but I had typed "peformance" for AC.

All is well here now.

Thanks you 5-HT for your suggestions.

---

### Post by 5-HT on 2007-07-18
I hate it when that happens...so hard to figure out (and I do it far too frequently, :()
Glad you got it working!

---

