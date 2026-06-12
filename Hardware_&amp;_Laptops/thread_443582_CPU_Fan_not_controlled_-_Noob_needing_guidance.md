---
title: "CPU Fan not controlled - Noob needing guidance"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Evilgiraffe on 2007-05-14
Hi there,

I'm new to Linux and need a little help getting my CPU fan under control.
The mainboard is an ECS SF2-M7. 

(Very little available info for the mobo as it's an OEM piece of kit installed into Philips Freeline MT1100)

A year or so ago I had to update the BIOS on this board to correct a RAM problem and ever since there has been no automatic fan control from the motherboard.

This wasn't a problem while I was running Win XP, as it was easily controllable with SpeedFan.  Now I've just installed Ubuntu (dual-boot, Feisty and XP) the fan is starting to deafen me again. :( 

Could someone give me some pointers to get PWM control of my fan?

Below is the output of "sensors" from lm-sensors

> it87-isa-0290
Adapter: ISA adapter
VCore 1: +1.20 V (min = +0.00 V, max = +4.08 V)
VCore 2: +2.58 V (min = +1.28 V, max = +1.68 V) ALARM
+3.3V: +3.25 V (min = +2.78 V, max = +3.78 V)
+5V: +4.97 V (min = +4.49 V, max = +5.48 V)
+12V: +11.58 V (min = +9.98 V, max = +13.95 V)
-12V: -1.47 V (min = -22.94 V, max = -17.05 V) ALARM
-5V: +0.01 V (min = -9.14 V, max = -7.75 V) ALARM
Stdby: +4.84 V (min = +4.49 V, max = +5.48 V)
VBat: +4.08 V
fan1: 4115 RPM (min = 664 RPM, div = 8)
fan2: 0 RPM (min = 664 RPM, div = 8)
fan3: 0 RPM (min = 664 RPM, div = 8)
M/B Temp: +48°C (low = +127°C, high = +78°C) sensor = diode
CPU Temp: +43°C (low = +127°C, high = +78°C) sensor = thermistor
Temp3: +21°C (low = +127°C, high = +78°C) sensor = thermistor
Many thanks in advance from a Linux N00b

EvilG

---

