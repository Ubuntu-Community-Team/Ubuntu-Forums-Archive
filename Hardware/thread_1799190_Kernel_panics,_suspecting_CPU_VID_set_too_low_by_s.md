---
title: "Kernel panics, suspecting CPU VID set too low by software"
date: 2011-07-07
forum: Hardware
---

### Post by Xianath on 2011-07-07
My system recently started crashing with a kernel panic. It's a Phenom II X2 555 CPU on a Gigabyte 870A-UD3 motherboard running a 10.04.2 x86-64 server with kernel 2.6.38-8-server. The system is well ventilated (8 fans total) and really cool (CPU at 36*C under full load), however it is not stable at all.

I suspect the CPU VID (cpu_vid0) may be too low at 1.050V but I have no idea **why** it is actually that low. I have Cool'n'Quiet disabled in the BIOS, voltage control is set to Manual and bumped up by 0.100V from its default of 1.275, and reported as such in the BIOS. However as soon as I boot Ubuntu, sensors report cpu_vid0 at 1.050V regardless of CPU frequency. It even stayed that way while doing a torture test in mprime!

So I guess my question is, does 1.050V seem too low for a dual-core Phenom II at 3200MHz, and if yes, how do I raise it from within Ubuntu and let the MB control it?

Thanks,
Peter

---

### Post by psusi on 2011-07-07
My guess is that you have a buggy bios that is passing incorrect VID values to the frequency scaling driver so as soon as it tries to scale down the cpu, the voltage is set too low.

---

### Post by Xianath on 2011-07-07
Thanks, I'll see if there's a newer firmware available. Failing that, are there any tunables to the voltage scaling driver?

---

### Post by Xianath on 2011-07-07
Nope, didn't work. Flashed the BIOS, and gave the stock 10.04.2 kernel a spin, no dice. I hope someone shares how one can tune the voltage scaling driver.

---

### Post by psusi on 2011-07-07
I think there was a program called k10ctl that might do it.

---

### Post by Xianath on 2011-07-07
Found it, installed it, and it reports the same VID as found in BIOS. I am quite certain that this is the correct voltage and the mobo sensors and/or Linux support are borked, since k10ctl is reading the MSR directly. Anyway, it's not voltage, which is probably bad news as I have no idea what it might actually be :( That, however, is subject to a different thread in a different forum. Thanks psusi, I learned something new today and eliminated one possible cause.

Cheers,
Peter

---

### Post by psusi on 2011-07-07
What exactly does k10ctl say?  I suppose it is possible that the sensors are wrong, but given the kernel panic, that seems unlikely.

Does the reported voltage seem to change the way it should when setting the cpu to different frequencies?

---

### Post by Xianath on 2011-07-08
k10ctl reports the VID as 1.275, which is what's set in the BIOS. Cool'n'Quiet is disabled and voltage control is set manually to the BIOS recommended value, and I don't see it change with frequency. It should change with temperature, but the CPU never gets hot enough for that to happen.

The reason I suspect a buggy sensor or just a misinterpretation is a certain temp3 of 80*C that the BIOS is completely unaware of.  Both the northbridge and southbridge heatsinks have been replaced with larger copper ones with dedicated 40mm fans spinning at over 5k RPM, the plastic clips and springs upgraded to M3 screws and the stock paste replaced with Arctic Silver 5. There's not a single place on the whole board that is even remotely hot to the touch, and those 80*C only fell down to 79 when I pointed 4x120mm fans directly at the board, and that value could easily be just a fluke.

---

### Post by psusi on 2011-07-08
The voltage is supposed to vary with frequency, not temperature.  k10ctl should report a different VID for each frequency, doesn't it?

Usually not all temperature sensors are actually hooked up to anything by the motherboard vendor, so it is not unusual for temp3 to give a bogus value, though usually it is something like 128 degrees.  Does the value still read 80 immediately after you wake the system up from being suspended for a while?  If so, then it's probably not connected.

---

### Post by Xianath on 2011-07-08
I might be wrong but since I have Cool'n'Quiet disabled and CPU Core Voltage set to Manual in the BIOS, they shouldn't change with frequency, right? As of VID changing with temperature, this I think is what the Hardware Thermal Control option in the BIOS does, though obviously I don't want to ever need to test it :)

I'll play some more with it when I get back home and confirm voltage scaling on or off (the box is off right now as I don't trust it enough to leave it running on its own.) I'll dust an old PC and use it as a serial terminal, hopefully I'll be able to catch some more kmesg information about the crash that way.

---

### Post by psusi on 2011-07-08
Cool'n'Quiet just means slowing down or stopping the CPU fan when it is cool enough.  The whole reason for lowering the cpu frequency is to allow the voltage to be lowered, and thus, save power and heat.

Each P-state on each CPU should have its own VID setting, with the higher P-states having a lower voltage.

---

