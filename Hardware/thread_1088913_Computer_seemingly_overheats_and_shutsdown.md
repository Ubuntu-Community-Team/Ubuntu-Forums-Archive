---
title: "Computer seemingly overheats and shutsdown"
date: 2009-03-06
forum: Hardware
---

### Post by rdoolen on 2009-03-06
My desktop computer has been shutting itself off without warning. I initially blamed the power supply and replaced it. However, this didn't fix the problem. In my attempt to isolate to issue, I installed lm_sensor. It seems that my CPU is getting so hot it shuts off the computer. But, I am not sure this is really happening. Sitting there doing nothing the temperatures of the CPU read ~2 oC, way below room temperature. I can ramp the temperature by running iTunes in VirtualBox – this uses enough CPU to cause the temperature to go up. It goes up to ~80 or 90 after a few minutes and shuts off the computer. The thing is, if I do this with the case open, I can't find anything inside the feels hot at all. The air blowing off the CPU is about room temperature. If I touch the CPU heat sink, it is warm but not hot. My laptop has run for years and you can fry an egg on that thing. So, I can't imagine why this computer should be shutting down. Also, If I pause the VirtualBox, the CPU usage goes immediately to zero, simultaneously, the CPU temperature returns to ~ 20 oC. This happens in less the 4 seconds. I admit I slept through most of Mass and Heat Transfer, but I can't think of many materials that can drop from 60-20 (in a 25 C room) in 4 seconds. 

I checked that the Heat sink for good thermal contact, and it seems to be fine.  Its a Micro ATX in an ATX case, so there is lots of room. Its a retail AMD CPU with the stock fan.

So, is my computer really getting hot someplace deep inside? If its not really that hot, how can I keep it from shutting down when it thinks its hot?

Here are some stats on my system:
GA-MA74GM-S2H
AMD Athlon 64 X2 5200+  2.7 GHz
Antec Sonata II case
Ubuntu 8.10 64-bit version

---

### Post by rdoolen on 2009-03-07
I tried some more stuff. I updated the BIOS. I also reseated the heatsink and reapplied the thermal paste. 

If I run it until it shuts down, upon reboot, the temperature in the BIOS also reads hot, like 80C. I think it may be an issue with the temperature sensors.

---

### Post by Skripka on 2009-03-07
> **rdoolen said:**
> I tried some more stuff. I updated the BIOS. I also reseated the heatsink and reapplied the thermal paste. 

If I run it until it shuts down, upon reboot, the temperature in the BIOS also reads hot, like 80C. I think it may be an issue with the temperature sensors.

My hunch would be a bum thermostat-the go bad ocassionally.


The stock AMD cooler stinks-no way it would sink 40C in 5 seconds with ~25C room temp air.

---

### Post by SkankinRatFink on 2009-03-07
Well, your CPU would never run below room temperature.

If your heatsink is cool to the touch, that could mean that you have a bad interface between the processor and the heatsink, thus trapping all the heat in the processor until it's shut down for protection. I would pull the cooler and inspect the surface, and re-install. (With new thermal interface material, of course.)

---

### Post by rdoolen on 2009-03-07
I did that. It seemed to be in good contact -- no obvious gaps in the paste. Also, the heat sink was fairly difficult to get off the CPU. I reinstalled with new silver paste (forgot the brand, but it suposed to be "the good stuff").

---

### Post by rdoolen on 2009-03-07
How could I tell if is a bad thermostat? Is there a way to fix it?

---

