---
title: "Dell Inpiron 1526 fan constantly cycles on-and-off, loud"
date: 2009-04-28
forum: Hardware
---

### Post by AlanDeSmet on 2009-04-28
I'm running Ubuntu 8.04.2 on my Dell Inspiron 1526, and as a general rule it's running like a champ.  It does have one annoyance I'm hoping someone else can help with: the fan regularly cycles on and off, even if the laptop is just sitting unused.  The CPU temperature will rise to about 53 degrees C, the fan will kick on and be quite loud for about 10 seconds, the temperature will quickly drop to about 47 degrees, the fan will stop and be silent.  30-60 seconds later, the cycle repeats.  (Temperatures are all from the Gnome sensors applet for the acpi/THM/CPU zone.  libsensors reports four more thermometers identified as "Core0" and "Core1" that run about 10 and 6 degrees cooler than the "CPU" entry.)  As best I can tell, the fan is cycling between full speed and dead stop.  As full speed is quite loud, it's annoying.   I'd expect the fan to have a "low" speed that it could spend more time at, reducing the amount of time it spends at full speed.

Searching for solutions, I'm seeing references to i8k utilities, but they don't appear to be available for my system, perhaps because I'm running a 64-bit kernel.  dellfand looks quite old, decidedly unsupported, and a bit risky; I'll try it if it's my only option, but I'm not keen on it.

Can anyone help me with my goal of a quieter laptop?  Let me know if there is more information I can provide.  Thanks for taking the time to at least look!

---

