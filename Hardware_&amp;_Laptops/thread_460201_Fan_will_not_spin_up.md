---
title: "Fan will not spin up"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by smyrna112 on 2007-05-31
ubuntu newb, Fan spins up at bois check and works fine in windows but will not spin in Ubuntu. want to keep this OS I love it!!! any suggestions?

---

### Post by Tilo on 2007-05-31
You have a laptop, I persume?? 

what's your cpu-speed??  type:

   cat /proc/cpuinfo

and check what speed it reports - newer LINUX systems which adjust the CPU frequency dynamically boot at 65..75% CPU speed..  I find this very annoying - especially if the laptop
is plugged in..   The reasoning behind it is to be at an optimum of power-consumption/cpu-speed/noise-level.. so it is _on_purpose_ that your fan does not spin up!!

You can change the cpu-speed like this:

   sudo cpufreq-selector -g performance

this should switch your CPU to 100% speed - and will result in the fan powering up.. 

cheers,

    Tilo

---

