---
title: "Problems with batery life"
date: 2008-06-16
forum: Hardware
---

### Post by genesiss on 2008-06-16
well i ave just installed Ubuntu 8.04
on my HP Pavillion zv6000 ( amd athlon 64 ) 
the thing is that when the laptop had windows 
it's battery usually lasted about 2 hours, now 
it barely last an hour... more like 50 minutes 
or so, I would like to know if there is anything 
I can do to make it last some more
I can't complaint on anything else... everything is 
working great so far, but it has a short battery life

thanks in advance

---

### Post by p_quarles on 2008-06-16
Try to find out which processes are using the most power. Normally, I would recommend powertop, but it is an Intel application, and may only work properly for Intel hardware. Perhaps worth trying, at least. Install it from the repositories, and then run it from the terminal with sudo.

---

### Post by sdennie on 2008-06-16
p_quarles advice is good and I recommend doing that but, also, just see if some application that you are using is constantly using the cpu.  While on battery, just open a terminal and type:

```

top

```

The display should be fairly self-explanatory and it's entirely possible that some app is just eating the CPU.

---

