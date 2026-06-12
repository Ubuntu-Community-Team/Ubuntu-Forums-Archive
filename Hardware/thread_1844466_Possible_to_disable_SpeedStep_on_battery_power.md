---
title: "Possible to disable SpeedStep on battery power?"
date: 2011-09-15
forum: Hardware
---

### Post by mexp on 2011-09-15
I have Dell Latitude D620 with Ubuntu 11.04. How can I disable the Intel SpeedStep when using the laptop on battery power? 

Now the CPU is constantly running on 1 GHz, when it could do double. In BIOS settings, it says that disabling the SpeedStep will put the CPU to a lower performance mode, and there's no other option...

---

### Post by diasf on 2011-09-15
You can always control manually the frequency. Or do a customized cpufreqd.conf.
To manually control the frequency, there are a number of interface plugins (for gnome, for unity - needs a ppa). 
I had to make a customized cpufreq configuration so my tablet wouldn't pass 100C idle... languague is a bit confusing at the start, but works like a charm
(you can, for instance, make the processor stay full power if a given program is running... its quite good)

---

### Post by mexp on 2011-09-15
Thanks for quick response :) I installed indicator-cpufreq (from [http://ubuntuguide.net/change-and-monitor-cpu-frequency-scaling-in-ubuntu-11-04-with-indicator-cpufreq](http://ubuntuguide.net/change-and-monitor-cpu-frequency-scaling-in-ubuntu-11-04-with-indicator-cpufreq)), but if I switch it to 2 GHz setting, it immediately falls back to 1 GHz... I wonder if the BIOS is more persistent in saving the battery than full performance?

---

### Post by diasf on 2011-09-15
It's not the bios, it is the deamon...... do a service cpufreqd stop first, then it will work

---

### Post by mexp on 2011-09-15
Uff, stopping the cpufreqd didn't help... I rebooted, and now I can switch between 1.00 and 1.33 GHz... 

I also tried disabling the SpeedStep in BIOS, then the freq really stays at 1 GHz, and the applet fails to load too.

---

### Post by diasf on 2011-09-15
Tbh what I don't understand is why would you need that? With an ondemand governor (and a proper cpufreqd.conf) it would go automatically to 100% when you need it and stay low otherwise (not much of a point running NOPs on the max frequency... even less on battery).

Anyway, I'm sure you can do what you want by editing the configuration of cpufreqd.

---

### Post by mexp on 2011-09-16
Well I have a reason: I use the laptop mostly with 12 V DC adapter (upping it to 18-19 volts). Apparently Dell laptops do not accept any other power sources but their original AC adapter, and the there's a startup message telling that the adapter is not the right one. I can still use it with 12 volts, but it's always on lower performance mode, that is, running on 1 Ghz instead of 2. I'm not sure if it's the Cpu or the Gpu,  but even some graphic/flash intensive web sites make some stutter, and this does not happen when I use mains, 220 V DC.

Hope this makes sense ;-)

What kind of configuration file should I try?

---

