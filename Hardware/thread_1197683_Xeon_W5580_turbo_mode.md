---
title: "Xeon W5580 turbo mode?"
date: 2009-06-26
forum: Hardware
---

### Post by ddobrigk on 2009-06-26
Hi, 

I just put together a system consisting of 2 Xeon W5580s and 24GB of DDR3 1333 RAM and installed Ubuntu 9.04 on it. It's working great, but I really wanted the Nehalem's turbo mode to be enabled. The W5580s are being cooled by two Thermalright Ultra-120 Extremes and there is certainly enough temperature headroom to make turbo mode work. 

But when I use the command to list available frequencies, all I get is:

cat /sys/devices/system/cpu/cpu11/cpufreq/scaling_available_frequencies
3201000 3200000 3067000 2933000 2800000 2667000 2533000 2400000 2267000 2133000 2000000 1867000 1733000 1600000

What did I do wrong? This CPU's scaling should allow it to go all the way up to 3600000 or, at the very least, 3333000 or 3466000. I disabled C1E and C-States in BIOS (after installing OS, mind you) but am still not getting the desired turbo-mode operation... I googled for any information about enabling turbo mode in linux, but didn't find anything really useful.

(Just out of curiosity, more detail and pics of the system can be found [at this link]("http://www.tomshardware.com/forum/262853-28-xeon-w5580-build"))

---

### Post by ddobrigk on 2009-06-26
Hum.... I just found [this link]("http://lkml.org/lkml/2008/12/15/189"), and it seems that 3201000 is not really 3201000: it just "tells" the hardware to go ahead and "gimme all she's got, scotty!" (sorry, couldn't resist)

So apparently when cat /proc/cpuinfo says 3201000, it is probably >3200Mhz, but the kernel doesn't really know what speed the hardware is running...

I was expecting to actually see the higher speeds. I guess turbo is working, then...

---

### Post by chowo on 2009-06-28
I believe that currently there is no circuit in the processor to retrieve frequency info. running in Turbo Mode.  The frequencies listed in the "scaling" are frequency to be switched among p-States.  You may question how some program can measure frequency running under Turbo Mode.  I can tell you that ... those are done by estimation ... i.e. measuring the time running 100 cycles and then project the CPU frequency that chip is currently running.
 
Once the Turbo Mode is enabled in BIOS, it then operates on its own based on the thermal conditions of the processor / cores.
 
I hope this answers your question ... :)

---

