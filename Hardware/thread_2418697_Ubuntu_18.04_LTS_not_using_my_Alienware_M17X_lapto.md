---
title: "Ubuntu 18.04 LTS not using my Alienware M17X laptop's CPU fan"
date: 2019-05-09
forum: Hardware
---

### Post by kevinrbrown on 2019-05-09
...So this, seems weird to me: 

Ubuntu simply will not use the CPU fan on my laptop to keep it cool. It has no problem finding and using the GPU fan, but finding and using the CPU fan apparently is a bridge too far. I've tried using lm-sensors  / fancontrol as well as the i8kutils software; these allow for fine tuning of the GPU fan, which is nice, but will not turn on the CPU fan. 

I've run the diagnostic utility on the machine's BIOS to confirm that, yes, the CPU fan is still working just fine so long as something tells it to run. Which Ubuntu won't do. :| 


There's no functionality in the BIOS that I can find to force the fan on. 


I don't suppose anyone has a solution for this? It seems like a pretty significant oversight is the building of an OS.

---

### Post by QIII on 2019-05-10
What is your hardware configuration?  The configuration of model numbers can change over the course of their lives.

Is your fan not running at all?  Is it being controlled by the BIOS?  Was this machine originally delivered with Windows?  Did it work with Windows?  Is the machine designed for Windows with such tight coupling that Windows was doing all fan control via software?

Sensors and the like can only detect and interact with what the mobo makes available.  If something is not available, it is hardly the fault of the OS.

---

