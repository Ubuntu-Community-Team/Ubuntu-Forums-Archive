---
title: "CPU frequency Stuck"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by qwerkus on 2007-06-06
hi,

I had to re-install completely my xorg server and xfce4 desktop because of a driver problem; since then the desktop works again, but the cpu frequency seems to bo stuck at 600Mhz although my centrino can clock 1.6ghz at AC power. Perhaps a vital power management packet has been drop during the reinstall ? What should I check for ? Can you manually set clocking configuration ?

Thanks for help,

qwerkus

---

### Post by Big_Croc7 on 2007-06-06
I can't help with the packages, but you might want to check that the throttling is not set:
```
cd /proc/acpi/processor/CPU1
cat throttling 
```
NB: it might be CPU0 instead of 1

This should show if your processor is being throttled.

More likely, its something to do with the frequency scaling and I'm not sure what to do there.

---

### Post by qwerkus on 2007-06-06
Thanks for replying. I don't know what really fixed it- but it works now. The cpu is being throttled again. Only difference is that it starts at 600 Mhz all the time, and adjusts frequency to usage, whereas it used to start at "full speed" while ac power plugged in. 
But i think I can live with that.

---

