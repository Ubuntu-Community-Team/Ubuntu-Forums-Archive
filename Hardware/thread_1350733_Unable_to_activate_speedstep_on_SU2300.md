---
title: "Unable to activate speedstep on SU2300"
date: 2009-12-09
forum: Hardware
---

### Post by helena_one on 2009-12-09
Hello,
I bought an HP-DM1 with SU2300 celeron core2duo CPU.
unfortunatly, I was unable to activate frequency stepping (acpi-cpufreq or whatever).

the SU2300 is supposed to integrate Enhanced Intel® Speedstep Technology so it should work.

when I add the gnome applet, it tells me that cpu frequency scaling not supported

anyone has a clue?

---

### Post by PatrickVogeli on 2009-12-09
yeah.. I'm afraid the only available frequency in the SU2300 is 1,2GHz.

---

### Post by helena_one on 2009-12-09
Hello,

may I ask where did you get this information from ?

I find no information in intel datasheet regarding only 1 frequency (while it is EIST compliant).


by the way, if I do 
```
cat /proc/acpi/processor/CPU0/throttling
```
It is sometime at T0 (100%) sometimes at T7 (12%).
do know what I should get from this...

---

### Post by PatrickVogeli on 2009-12-09
I have a SU4100 and my girlfriend a SU3500. My SU4100 has only 2 freqs: 1.2GHz and 1.3Ghz, when I actually expected to also have 800MHz. My girlfriend's SU3500 has 1.4, 1.2 and 800Mhz.

The freqs are also checked in windows, and the same happened.

To go lower than 1.2GHz the processor must have Dinamic FSB, so the FSB switches down to save more power getting lower freqs. The cheaper Intel procs don't have that.

Actually, that isn't such a deal breaker.. It may save some power, but not that much.

Throttling isn't what you are looking at. The most important things are C-States (when the proc is idle, higher C state means less power usage) and P-States (the freqs).

---

