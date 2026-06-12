---
title: "Centrino locks at 680MHz"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by erlingwl on 2007-05-22
I've just upgraded from Edgy to Feisty and everything seemed okay. But after a while (30mins +) of use (playing movies, surfing etc.) the CPU speed won't go above 600-680 MHz even if I try to force it to (using CPU frequency monitor..). Of course my laptop gets very warm of heavy use, but it has never behaved like this before.

Does anyone have a hint to where I might look to find a solution for this problem. It is really frustrating to watch a movie, and suddenly the movie starts to slow down and hang..

---

### Post by matburton on 2007-05-23
Are you using the CPU frequency applet?

If so what governor are you using?
(It's the first word when you hover over the icon like "Ondemand 798 MHz (40%)"

If its ondemand I can't help you :???: sorry but worth a shot

EDIT:
You can check if you can set your frequency to maximum by using the following
```

sudo cpufreq-selector -g performance

```
What frequency does that give you?
You can set the governor back using the same but replacing 'performance' with 'ondemand'

---

