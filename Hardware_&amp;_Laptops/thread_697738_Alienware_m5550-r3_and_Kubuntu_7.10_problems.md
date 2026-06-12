---
title: "Alienware m5550-r3 and Kubuntu 7.10 problems"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by dusted on 2008-02-15
Hey, I've recently upgraded from an Acer Travelmate 2420 to an Alienware m5550, I used the Kubuntu 7.10 x86 DVD and it installed fine, I enabled the restricted driver for my ATI x1400 card and can use the 1280x800 resolution.  Now comes the problems, the volume up.down keys control the headphone channel which actually does nothing, when plugging in headphones, the speakers are still giving output and both the PCM and front channels control the volume of both the speakers and headphone jack.  The OSD for the volume up/down does work, it is just mapped to the wrong channel, also when I plug in headphones I would like the speakers to turn off.  There is also a hardware dial on the side of the laptop which controls the volume level in Windows, would be nice to have this functionality in Kubuntu.

Here's the output from "lshal -m"
14:24:21.796: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = volume-up
14:24:22.053: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = volume-down
14:24:22.877: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = mute

The second problem is Suspend and Hibernate both don't work, it flashes my screensaver for a split-second then screen goes black and the computer freezes requiring me to hold the power-button to turn it off.

Third problem is just a minor one, the screen brightness can only be controlled from the function keys on the keyboard, the power manager's brightness settings do not affect the screen brightness.


Thanks in advance for any help.

---

### Post by dusted on 2008-02-18
I'm still stumped on this one, anyone else have an Alienware m5550-r3 that can help me out?

---

