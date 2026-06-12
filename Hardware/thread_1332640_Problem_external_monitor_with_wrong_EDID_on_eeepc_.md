---
title: "Problem: external monitor with wrong EDID on eeepc 1005 (karmic)"
date: 2009-11-20
forum: Hardware
---

### Post by ignaciouy on 2009-11-20
Hi everyone,

I've been trying to solve this on my own but I am just not getting it:

I would like to plug my external monitor (Benq 900wa) to my eeepc 1005ha to get an extended desktop, but my monitor sends the wrong EDID so I'm not able to choose the right resolution for it (1440x900, I get 1360x768 maximum).

The new X does not use an xorg.conf, which I think is great, but I would need one to add the modelines for my external monitor.

I tried generating an xorg.conf for my hardware (and to modify it with the new modeline) with

```
sudo Xorg -configure
```

but the resulting xorg.conf was a mess (at least I didn't understand it).

I also tried following the instructions found [here]("http://forums.vr-zone.com/notebooks-netbooks/491578-howto-ubuntu-linux-users-using-netbooks-external-monitors.html") (it involves using xrandr to add and switch modes instead of using an xorg.conf), but my X went completely down (and took the rest of the OS with it) when trying to switch to the newly added mode (heard that there's a problem with the new intel driver maybe?).

So all in all, what do you suggest to get my external monitor working?

Thank you very much!!

---

### Post by ignaciouy on 2009-11-25
No one? It's a valid problem

---

