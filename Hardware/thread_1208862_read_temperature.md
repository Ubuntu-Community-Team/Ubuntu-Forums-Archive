---
title: "read temperature"
date: 2009-07-09
forum: Hardware
---

### Post by oh my on 2009-07-09
Hi,

I have a Acer Travelmate 6492, I installed lmsensors and let it configure. However it doesn't show the right temperatures (only 0 &1 °C)

Is there another tool to get the correct temperatures for my hardware?

regards

---

### Post by oh my on 2009-07-10
Or if there is no other way of checking temperature in linux, could you tell me what I can do to get lm-sensors to work properly on my laptop?

This is the outpout I get:
```
   acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.0°C  (crit = +107.0°C)
temp2:        +0.0°C  (crit = +106.0°C)
temp3:        +1.0°C  (crit = +106.0°C)
temp4:       +48.0°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +13.0°C  (high = +100.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +0.0°C  (high = +100.0°C, crit = +100.0°C)

```

---

### Post by oh my on 2009-07-15
Hi,

anyone got any ideas how to fix the wrong temperatures? I really need help with this, it's rendering my laptop unusable.

---

### Post by bichopro on 2009-07-15
Sorry my bad English..

here is the max temp of the cpu: [http://www.pantherproducts.co.uk/Articles/CPU/CPU%20Temperatures.shtml](http://www.pantherproducts.co.uk/Articles/CPU/CPU%20Temperatures.shtml)

the gpu temp is variable, ati, nvidia and intel graphics have different max temp

the max temp hdd temp is 55 o 58 ºCelsius in a laptop.

laptops normally is more hot than a desktops

---

### Post by oh my on 2009-07-15
Thanks for the answer.

I have a t8300, max temperature is 105 °C (see here: [http://www.cpu-world.com/CPUs/Core_2/Intel-Core%202%20Duo%20Mobile%20T8300%20EC80577GG0563M.html](http://www.cpu-world.com/CPUs/Core_2/Intel-Core%202%20Duo%20Mobile%20T8300%20EC80577GG0563M.html) )

THe problem is here:
> 
Core 1:       **+0.0°C**  (high = +100.0°C, crit = +100.0°C)Current temperature of the CPU is not 0°C even if sensors says it. How do I get the real value? (30-40°C)

---

### Post by oh my on 2009-08-08
How do you get help here? What do I have to do?

---

### Post by oh my on 2009-08-21
up

---

