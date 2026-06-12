---
title: "Reinstall powernowd or install cpufreqd"
date: 2008-08-24
forum: Hardware
---

### Post by trekkie00 on 2008-08-24
I started folding on my laptop, and powernowd kept cutting back the CPU speed. So, I tried cpufreqd, but didn't find how to set it up. Now, I can't reinstall powernowd - it comes up with an error:
"/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:No such file or directory."

I'm running a Core 2 Duo T5670, 1.80ghz. It worked fine until I tried messing with it.

Although I would like to get power management working again, I'm not real particular on how. I would, however, like it to only cut back the CPU speed while on battery power - why do it while it's plugged in?

Any advice on getting it to do this (and installing it) would be greatly appreciated.

---

### Post by Sam Lars on 2008-08-24
I used to use the gnome-panel applet, but now that I use AWN instead of gnome-panel, I'm using cpufreqd.  It seems a bit less reliable, as it seems to keep wanting to go to performance while on battery though I've told it in power manager and on command line to go to conservative (opposite problem of yours?).
I have noticed behavior similar to yours, though.  You should check to make sure that it's still applying the governor you want, and also look at the max scaling frequency to make sure it's at full.  It could also be that your fan is working as hard as it can and it's scaling to keep the temperature down, I think that happens to me.
As for the package problems, have you made sure that the package is completely removed and has no residual configuration files?  I find the best way to check for this is with Synaptic.

---

### Post by trekkie00 on 2008-08-24
I went into Synaptic package manager and completely removed the powernowd program and then reinstalled it, and it seems to be working normally now. THanks!

---

