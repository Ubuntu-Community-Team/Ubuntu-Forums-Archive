---
title: "Weird idle CPU usage"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by Moosferatu on 2007-04-16
I've been watching my CPU usage and temperature on my Inspiron 6000 recently, and noticed something odd.  Normally the system idles at around 40-42C with 0-2% CPU usage, but after five minutes of idling out of nowhere the CPU usage jumps up to 70-100% and the temperature goes up by around 20C.  This is really irritating since I leave my computer running for long periods of time and would prefer if it were sitting around at 40C and not 60C.  What pressing process does the CPU feel like it needs to run while the system is idle and how can I stop it?

---

### Post by joft on 2007-04-16
Well, identifing the process, which causes such a big load (70-100%), should be as easy as invoking "top" (in a terminal window). It displays all processes ordered by load (by default).

---

### Post by Moosferatu on 2007-04-16
Yeah, should have thought of that.  Turns out it's Beagle.  I don't really use Beagle all that often so I think I'll just remove it.  Thanks.

---

### Post by kingy89 on 2007-04-16
Wow!

I just checked and my Beagle does the same, it must be archiving stuff or something. 

Thanks for letting me know!

---

