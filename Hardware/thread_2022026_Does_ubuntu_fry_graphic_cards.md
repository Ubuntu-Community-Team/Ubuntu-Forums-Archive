---
title: "Does ubuntu fry graphic cards?"
date: 2012-07-10
forum: Hardware
---

### Post by Charles_B on 2012-07-10
[FONT=Arial]Hello
[/FONT]
[FONT=Arial]just a week ago my graphic card started acting funny again. The screen freezes now and then (getting more often nowadays) with lots of vertical and horizontal lines. This happened to me for the third time: first with a NVIDIA on a personal computer, than with some ATI card on a ThinkPad laptop and now with an Intel card on a HP laptop. Is it possible that Linux is responsible for that? That it fails to control the temperature of the card or something similar?[/FONT]

---

### Post by Ubun2to on 2012-07-10
The GPU temperature is controlled by the fan. I highly doubt all these fans are failing.
The fact that this has happened on an Intel, NVidia and ATI leads me to believe it's a driver problem. Go to the Additional Drivers program and enable them if they aren't already enabled.
Also, Intel does Integrated Graphics, which are graphics built into the CPU (no video RAM, unlike NVidia and ATI GPUs); it works great for AisleRiot Solitare, but don't expect to be able to play BF2 with high quality graphics.
So, just try going to Additional Drivers, enable any that aren't already turned on, reboot, and see if that solves the problem.

---

