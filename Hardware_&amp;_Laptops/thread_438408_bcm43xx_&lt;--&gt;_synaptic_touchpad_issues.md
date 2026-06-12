---
title: "bcm43xx &lt;--&gt; synaptic touchpad issues"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by hatchek on 2007-05-09
I'm installing Feisty on an HP dv8000 laptop. 
I'm having a strange issue with the bcm43xx wireless driver and my snyaptics touchpad.

It seems, whenever the wireless card is configured by the operating system, the mouse acts funny, skipping around the screen, producing random clicks
When this driver is not present, or the radio is not on, the mouse problem goes away.
The messages where the driver loses its sync also only appear in dmesg after the bcm43xx driver is loaded. 
[ 2111.664000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2111.668000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2111.668000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2111.668000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2111.684000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
etcetera, etcetera.

Any thoughts?

---

### Post by nachotronics on 2007-05-17
A walkaround might be blacklisting the bcm43xx driver and using ndiswrapper with the windows driver.

---

