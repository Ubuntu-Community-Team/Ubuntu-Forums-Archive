---
title: "speedstep frequencies"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by djoelsson on 2006-07-12
Hi,

*cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies*

gives me:

*1733000 1333000 1067000 800000*

Is there a way to change these frequencies or are they a property of the processor (core duo 1.73GHz)?  In windows I have eight different settings.  I'd like to idle just above 0 if possible.

Thanks,
Dan

---

### Post by reacocard on 2006-07-12
put a "cpu freqency scaling monitor" on your panel, then do:
```
sudo chmod +s /usr/bin/cpufreq-selector
```
now click on the icon to get a list of freqencies you can change to. if you change the preferences of the applet you can get a list of cpu governers as well.

---

### Post by djoelsson on 2006-07-13
Done that already.  Same frequencies show up there as well.  I can't seem to go lower than 800mHZ.  I wonder if it's a hardware limitation?  I actually haven't checked in windows to see if I can get lower than that.

Thanks for your reply,
Dan

---

### Post by reacocard on 2006-07-13
it is a hardware limitation. the speedstep frquencies are built into the chip.

---

### Post by djoelsson on 2006-07-13
Ok thanks,

Is there anyone else reading this thread that has a 1.73gHz core duo centrino?  If so, are your frequencies the same?

Dan

---

