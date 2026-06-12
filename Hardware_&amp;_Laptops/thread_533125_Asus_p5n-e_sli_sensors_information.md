---
title: "Asus p5n-e sli sensors information"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by mavicus on 2007-08-23
Does anyone have configuration information on the sensors in the p5n-e sli motherboard?
I have followed the instructions for setting up lm-sensors and I have confirmed which readings belong to the "CPU temp", "motherboard temp", and fan speed. (a no brainer)

All voltages come back reported as 5v ranges, but I think some need re-calibrating to the correct ranges.
Also, there is a 3rd temperature reading that always reads 25C, but does not show up in the bios with the other 2 voltages. It reads at 25C even when the other voltages fluctuate by 10C. So I must wonder what in the world it really is there for.

Any help is appreciated

---

### Post by linuxwizard on 2007-08-24
[http://www.lm-sensors.org/wiki/Configurations/Asus/P5N32-E%20SLI%20Plus](http://www.lm-sensors.org/wiki/Configurations/Asus/P5N32-E%20SLI%20Plus)

---

### Post by mavicus on 2007-08-26
Thank you very much sir!

For others who may tread here, the solution given here is for the P5N32-E SLI Plus, and works also for my P5N-E SLI.

My motherboard has one additional chassis fan so I added the following line to the configuration.

> label fan3 "CHA FAN Speed"

---

