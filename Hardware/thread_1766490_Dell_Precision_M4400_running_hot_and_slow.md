---
title: "Dell Precision M4400 running hot and slow"
date: 2011-05-24
forum: Hardware
---

### Post by thundre on 2011-05-24
I believe I have solved the problem by upgrading to 11.04 and not installing the NVidia proprietary driver.

The problem configuration:

* Ubuntu 10.10
* Gnome
* Firefox
* Flash installed but disabled most of the time

The trigger seems to be using Facebook on Firefox.  Facebook uses a ton of Javascript.  I knew it wasn't a pure hardware problem because it didn't happen on Windows XP on the same machine.


The symptoms:

The laptop fan would go to high speed.  Applications would then run slow, even lightweight ones would show high CPU usage in "top".  Once it was in this state, it would not fix itself without a power-off.

Solutions that didn't work:

* Quitting applications
* Rebooting without a power-off
* Switching to Google Chrome
* Removing the nvidia packages

Finally I tried upgrading to Natty.  The first time it booted, it went into text mode and I found out that xorg.conf specified the "nvidia" driver, which was not in my new Natty kernel.  Once I removed xorg.conf it ran fine (1.5 days so far, knock on wood).

I still don't understand why an overheating GPU would make the CPU turn inefficient.  But I suppose anything's possible in the kernel.  I'd like to understand more about this kind of thing, if anybody has pointers or similar experiences.

---

### Post by yossell on 2011-05-24
I may be totally wrong, but this may not be a linux issue. If, like my laptop, your cpu and graphics chip are attached to the same heatpipe, then an overheating gpu can cause the cpu to get hot too as the heatsink become ineffective. If the cpu gets too hot then (?) the bios might start throttling cpu for protection. 

But this is just a guess.

---

