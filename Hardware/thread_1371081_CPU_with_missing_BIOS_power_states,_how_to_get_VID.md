---
title: "CPU with missing BIOS power states, how to get VID? Maybe with cpufreq?"
date: 2010-01-03
forum: Hardware
---

### Post by dreamdust on 2010-01-03
My CPU has missing power states in my BIOS. I'm in the process of patching my DSDT to add them in myself.

I found the different frequencies my processor runs at, but my question is there a program to get VID values from power states in use through the MSR? I need the actual VID's used for each frequency in order to patch my BIOS...

Does cpufreq have a way to list these?

I found this program that gives me the current FID/VID in use ([http://www.ztex.de/misc/c2ctl.e.html](http://www.ztex.de/misc/c2ctl.e.html)), but to get the other pairs I need to change CPU frequency and cpufreq-selector -f 1600000 doesn't do anything.

---

