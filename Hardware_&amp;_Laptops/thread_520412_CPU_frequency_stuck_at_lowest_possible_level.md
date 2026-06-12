---
title: "CPU frequency stuck at lowest possible level"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by Mr. Swiveller on 2007-08-08
Hello everyone -

My laptop is suffering from a bug reported here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88899](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88899).

Until recently, I could switch my cpu's frequency from 800 Mhz to 1.8 Ghz and back again by changing the CPU frequency policy through KPowersave. Unfortunately, this is no longer the case - my CPU's frequency is ALWAYS at 800 Mhz, irrespective of the frequency policy that has been set. The output from

scaling_driver
scaling_governor
scaling_(min|max)_freq
scaling_setspeed
scaling_available_governors
scaling_available_frequencies

appears to be correct - three steps are reported: 800 Mhz, 1.6 Ghz, and 1.8 Ghz.

Does anyone know whether I can force my CPU to run at 1.8 Ghz through a terminal command and/or (KDE) applet? A permanent fix would be wonderful, yet since many other people are reporting the same bug, I have put my hopes in a 'quick fix' which will allow me to accelerate the laptop if/when necessary.

Regards,

Swiveller

---

