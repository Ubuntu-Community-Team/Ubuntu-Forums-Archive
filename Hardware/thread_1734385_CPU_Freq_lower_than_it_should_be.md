---
title: "CPU Freq lower than it should be?"
date: 2011-04-20
forum: Hardware
---

### Post by Wild-Storm on 2011-04-20
Hi,
I have a Intel Core2 Duo E8500 which provides 3.16GHZ on each core. When looking at /proc/cpuinfo or using sysinfo, it shows me that the cores actually only are at 3000.000 MHz. I am not using cpufreq but speedstepping is available. When I use the cpufreq GNOME applet I only can switch between 2GHZ and 3GHZ, so no 3,16GHZ.

So what could be the problem?

---

### Post by TBABill on 2011-04-20
Cpufreq is now part of the kernel settings since 10.04 I think. You can check your settings via terminal by doing ```
cpufreq-info
``` and it should list in quotes what your actual setting is plus the various available frequencies. The GUI is ok I guess, but I tend to trust the terminal results more and I always make the changes to the settings via terminal. 
 
If you aren't seeing the max speed you should be running, perhaps your cpufreq setting is incorrect or your power settings could be affecting it. I'm not certain on that one, but something to check anyway. And whether you are on battery or AC if it's a laptop.

---

