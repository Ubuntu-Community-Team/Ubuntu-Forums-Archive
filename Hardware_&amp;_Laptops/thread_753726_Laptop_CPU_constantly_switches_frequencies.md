---
title: "Laptop CPU constantly switches frequencies"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by enbuyukfener on 2008-04-13
I've been running Ubuntu for about 6 months but in the way of power management, I have kept things mostly as is besides some "time before shutting down", "turning off displays" etc. So it is mostly a stock setup.

The problem is that the frequency of the CPU constantly switches between 800MHz and 1801MHz modes with the rare occurrence of in between values such as 1200MHz.

I am not sure if this started happening recently however I suspect it has been going on for awhile as it would explain the fluctuations when viewing System Monitor (my previous method of resource consumption monitoring)

The changes occur every 1-2 seconds. Nothing seems to change this behaviour such as bringing CPU and memory consumption to a minimum by removing most processes.

Some more info:
- Monitoring primarily with [conky](http://conky.sourceforge.net/) at the moment
- Core2Duo 1.8Ghz CPU
- Hardy / 2.6.24-15-generic kernel (should this be an i386 or i686 version? I don't seem to see an i686 version and cannot find much info on this)

I don't know of any outputs I should be providing though due to my limited knowledge, I'll guess some but these are probably redundant or irrelevant:
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1801000 1800000 1200000 800000

$ cat /sys/devices/system/cpu/cpu1/cpufreq/affected_cpus
0 1

$ cat /sys/devices/system/cpu/cpu0/cpufreq/stats/time_in_state 
1801000 3068640
1800000 132030
1200000 253743
800000 5724097

$ cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate
80000
```

---

### Post by hyperair on 2008-04-13
Sounds to me like you inadvertently turned on CPU Frequency Scaling. Add the CPU Frequency Scaling monitor applet to your gnome-panel. It'll allow you to monitor your CPU's frequency, and also manually change it.

---

### Post by RTrev on 2008-04-13
Perhaps you could go into configuration editor and see what your policy_ac is set to.  I believe it defaults to on_demand, which usually works well for me.  You could try some of the others, though, such as conservative.

Or, maybe it's just screwed up.  I can't think of any situation where my scaling has changed as often as you're describing.  Perhaps keep an eye on system monitor and see if something is constantly asking for and then releasing the cpu?

Bob

---

### Post by kerry_s on 2008-04-13
sounds normal to me lowers when not needed, rises when needed, suppose to save power, increases cpu life span. i have a 450mhz, mine goes down as low as 7mhz when not needed.

---

### Post by hyperair on 2008-04-13
I think your sampling rate is a little off. Mine's set to 1000000.

---

