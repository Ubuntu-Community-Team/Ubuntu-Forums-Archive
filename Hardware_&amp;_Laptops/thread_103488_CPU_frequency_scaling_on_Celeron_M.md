---
title: "CPU frequency scaling on Celeron M?"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by rotte2 on 2005-12-14
Hi

I've got a Celeron M processor, and I would like to use CPU frequency scaling for power saving, but I've not managed to find any howtos. Is this feature compiled into the kernel in the standard Ubuntu installation? How do I enable the feature, as my /proc/cpuinfo tells me, that the frequency is now 1.3 MHz? :confused:

---

### Post by 23meg on 2005-12-14
What's the maximum speed of your processor? See if you have powernowd running in System Monitor, and if not, try launching it with ```
sudo powernowd
```. 

The following command will let you switch frequencies manually with the Cpu Frequency Scaling Monitor (in the Gnome panel) while powernowd is off```
sudo chmod +s /usr/bin/cpufreq-selector
```See if you can switch frequencies after you restart the applet.

---

### Post by rotte2 on 2005-12-14
Couldn't find the powernowd in the System Monitor. Tried to restart the powernowd:

```

# /etc/init.d/powernowd restart
 * Stopping powernowd:                                                   [ ok ]
 * Starting powernowd...  
* CPU frequency scaling not supported

```

Does this mean, that CPU frequency scaling is not supported by the processor, or is it not built into the kernel?

```

# sudo powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace  modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,  and that it works. (check dmesg for errors)

```

Any attempts to use the cpufreq-selector gives the same result:
```

No cpufreq support

```

What do I need to make cpufreq works? :(

---

### Post by 23meg on 2005-12-14
The processor can do it. Add the line ```
p4_clockmod
``` to your /etc/modules file, reboot and try again.

---

### Post by rotte2 on 2005-12-14
Edited the modules-file and rebooted, and I got the /sys/devices/system/cpu/cpu0/cpufreq directory (which I didn't have before). 

```

# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
162500 325000 487500 650000 812500 975000 1137500 1300000

# cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
162500

```

It works! :D 

23meg - you're the best!

---

### Post by 23meg on 2005-12-14
Glad I could help; see the manpage for powernowd if you'd like to customize or disable it.

---

