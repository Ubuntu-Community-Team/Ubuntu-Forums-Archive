---
title: "gkrellm and hardware sensors"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by gcranston on 2005-06-08
I've been playing with gkrellm for a while on a Dell Inspiron 2650.  I can get most of it going alright, all of the builtin krells are great except the hardware sensors (well, the battery too, but this is more pressing).  Under the info tab it says "No sensors detected".  Now I know that somewhere I must have hardware sensors(temp, woltage, fan speed).  I can't find any sensor info under BIOS.

I did try a couple things as a fix.  I've installed lm-sensors, libsensors3 and libsensors-dev from apt.  I also tried a bunch of other sensor programs off apt and all came back "no sensors found" in some form or another.  I can't find any kind of kernel module loaded for the sensors, which makes me think the problem is there, but don't know how to load one if I even have it.

I think that covers it... help please!!

---

### Post by elv on 2005-06-09
After installing the lm sensor, do : sudo sensors-detect
That should configure it for you








edit: forgot to mention, you need to reboot after so the modules get loaded

---

