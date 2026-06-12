---
title: "aOpen MP45 and cpufreq"
date: 2009-03-10
forum: Hardware
---

### Post by Danneman on 2009-03-10
My first post to this forum. Hi everyone :D

I'm setting up a htpc based on aOpen MP45 (which is a REALLY nice little computer if you ask me), Ubuntu 9.04 64 bits (alpha obviously) and xbmc. After a few days of tweaking it's becoming a very pleasant htpc. Currently I'm struggling with a problem that's driving me insane though. No matter what I do I can't seem to get cpufreq to work.

The machine is equipped with an Core2Duo P8400, which supports enhanced Speedstep if I understand things correctly. cpufreq-info tells me the following though:

```
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
```

The only relevant module I can find is speedstep_lib and that's loaded. While googling about this I've read about other modules that supposedly should be loaded, like acpi_cpufreq or speedstep_centrino but none of them seems to exist in my kernel (?). Installed kernel right now is 2.6.28-8-generic.

Looking in /sys/devices/system/cpu/cpu0 I find no cpufreq directory, which also seems strange.

Oh, and I've also searched BIOS settings. Found nothing that seemed relevant...

Anyone got any ideas? Anyone got frequency scaling working on this machine?

Pulling my hair...

/Daniel

---

### Post by Danneman on 2009-03-11
I guess something must have changed radically between intrepid and jaunty. linux-image-2.6.27-11-generic in intrepid has loads of cpufreq related modules, linux-image-2.6.28-8-generic had only two. If things changed like this, why am I unable to find any information about it? Strange...

Not much hair left now :(

/Daniel

---

### Post by Danneman on 2009-03-11
Ok. Now I know that from 2.6.28-8.25 the cpufreq stuff is not modules anymore but is compiled straight into the kernel. Explains why I didn't find any modules.

It doesn't explain though why the scaling refuses to work. I'm back to square one. Darn.

Is it the chipset (intel G45) that's the problem? Or have aOpen put some evil turn-off-speed-step-for-people-not-running-vista code in their BIOS? Questions are many, answers are few. Think I should start writing a blog about this...

/Daniel

---

### Post by Kalderama on 2009-07-10
Having the same issue on 9.04 with core2duo E8400. Any help out there?

---

### Post by Danneman on 2009-07-10
Well, I simply gave up. Couldn't find any way of getting it running ](*,)

/Daniel

---

