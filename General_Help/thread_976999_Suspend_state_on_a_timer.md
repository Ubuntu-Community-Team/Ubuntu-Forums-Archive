---
title: "Suspend state on a timer?"
date: 2008-11-09
forum: General Help
---

### Post by blueherring on 2008-11-09
I want to set up a low power server that runs infrequent timed scripts.

I've got an Ideq box with a Sempron processor and I've gotten it down to 47 watts in powersave mode with cpufreq-set, but I'd really like to average 5 watts.

The lowest frequency I've gotten is down to 1000, I haven't tried to edit the params that control that, it sounds like perhaps that's the lowest supported frequency for the hardware.  Voltage is also reduced somewhat.

I think I'd rather try to do a timed suspend, have never tried to use suspend on UBUNTU nor done a timer to control that, wonder if it is possible and if so what utilities I might look at to try to do it?  I'm fairly resourceful if I can find a starting point.  I think I'm trying to get into ACPI state S1, and have a hardware timer set to resume.  If I can't get that, anything that might knock off 10 watts or so would be appreciated.  Performance is not an issue, at least not if I can change states within a few seconds.

Thanks much =

BH

---

