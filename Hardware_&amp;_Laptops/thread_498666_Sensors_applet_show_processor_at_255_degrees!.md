---
title: "Sensors applet show processor at 255 degrees!"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by cogadh on 2007-07-11
I've got lm-sensors installed and running and I just put the sensors applet on the panel. Right off the bat, I get a red flag on my processor, specifically CPU_PWM, showing it is at 255 degrees C! I also have a different indicator, CPU Temp, showing it at 35 degrees C, which sounds a lot more reasonable. Does anyone know what the CPU_PWM sensor is actually supposed to report? I know it can't be the correct temperature of any part of my PC, you could bake a cake at 255 degrees C and I think I might feel that kind of heat with the PC right next to my left leg.

---

### Post by Vajra Vrtti on 2007-07-11
I don't know the exact meaning of the CPU_PWM value, but it certainly does not mean 255°C. PWM means *Pulse Width Modulation fan control*, so CPU_PWM has to do with the CPU fan control, and 255 means 100%. If you google for CPU_PWM you will see that 255 is a pretty common value.

---

### Post by cogadh on 2007-07-12
Interesting, that makes a lot of sense now. Still, the sensor applet shouldn't have defaulted to using a temperature indicator for that particular sensor. I'll have to look into that one later. Thanks for the response!

---

