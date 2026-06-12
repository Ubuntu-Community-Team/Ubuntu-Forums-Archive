---
title: "Using an external monitor"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by bobfrommarketing on 2007-02-05
I have a Travelmate 2420 that I just installed Edgy on. It has an Intel 915 card, and runs a native resolution of 1280x800. Everything is fine and dandy out of the box.

Now I'd like to plug an external monitor into it, I have no intention of expanding the desktop over a second monitor or anything fancy, I just want to use an external mouse, keyboard and monitor in a docking-station kinda way.

My monitor is a LG Flatron L1710M, with a 1280x1024 resolution. I found a post describing how to add desired resolutions in xorg.conf, and I did that so I can change resolutions just fine. 

My problems are;
I can't figure out how to "hot-swap" between laptop display and external display. In Windows there's a key-combo to swap, but I'm sure that is a driver thing. Right now I have to boot Windows, swap and reboot into Linux. The key-combo in Windows is CTRL+ALT+F1 and F3, which obviously gives problems in Linux anyway.

Even though I can change resolutions, it doesn't look right on the external monitor. I think it's trying to cram the resolution onto the settings for the laptop display, how do I make it recognize the external monitor?

Not sure if this is a problem, but in xorg.conf there's a line that says "driver", and it's showing 810, not 915.. is that a problem? It works alright, so I'm just curious.

Thanks in advance

---

### Post by bobfrommarketing on 2007-02-08
Please guys, someone's got to know how to do this!

There's a ton of posts asking how this can be done, no answers, can it really be that it can't be done?

Given the amount of posts about this, I would vote for getting the answer a sticky somewhere, or into the FAQ.

---

### Post by brettr on 2007-02-08
Hey, What exactly is the problem? Is it working or is it just the hot-swapping problem. It might be the Horizontal synch and vertical refresh rates are not being detected, rather then the resolution. I am not familiar with how X treats hotplugging and unplugging monitors.

Anyways to set the rates you need to edit your /etc/X11/xorg.conf and add something like:
```
 HorizSync       30-80
VertRefresh     50-75

```

to the relevant Monitor section, depending on what the rates are for your particular monitor.

Hope this is of some help

---

### Post by bobfrommarketing on 2007-02-10
> **brettr said:**
> 
to the relevant Monitor section, depending on what the rates are for your particular monitor.


Well the problem, as described, is both the hotswap thing, and how to make a second monitor appear in xorg.conf. I only got one showing, my laptops.

---

