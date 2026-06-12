---
title: "CPU Temperature Sensors"
date: 2013-08-10
forum: Hardware
---

### Post by abrake on 2013-08-10
Hi, I've been trying to monitor my system temperatures but I'm having trouble interpreting the output of sensors:

```
f71808a-isa-0600
Adapter: ISA adapter
+3.3V:        +3.31 V  
in1:          +0.90 V  
in2:          +0.96 V  
in3:          +1.08 V  
3VSB:         +3.33 V  
Vbat:         +3.30 V  
fan1:         834 RPM
fan2:        1535 RPM
fan3:           0 RPM  ALARM
temp1:        +47.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = thermistor
temp2:        +53.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +25.4°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)
```

Presumably one of the temperatures is my cpu and the other is my motherboard but I want to know if anyone can tell me which one is which. Scanning through forums I've noticed that sensors can sometimes get an output like Core 0 or Core 2 for their cpu temperatures, so I'm wondering if it is a problem with sensors-detect. Any help is appreciated!

CPU: AMD A10 5800k
MOBO: MSI FM2-A75IA-E53 Mini ITX FM2 Motherboard

---

### Post by tgalati4 on 2013-08-10
The AMD A10 is a quad-core processor.  It's possible the temperature sensors are on the bottom and top of the overall CPU die, that would be consistent with 47C at the bottom and 53C at the top.  You would have to dig into the details of your CPU and motherboard to find the thermistors.  Look on the motherboard for "T1" or "TH1" or "THM1".

If you have on-board graphics, then one could be the CPU and the other the GPU.  It's also common to have a CPU temperature sensor and one near the on-board power supply that supports the CPU.

---

### Post by abrake on 2013-08-10
I've intensively scanned an image of my motherboard (I'm too lazy at the moment to open up my case and unplug everything), but couldn't find anything. I also took a look through the motherboard manual but didn't find anything in there about temperature sensors either. 

When I'm in the BIOS there is a CPU and a motherboard temperature listed, but I can't determine which temperature there correlates to temp1 or temp2 from sensors.

---

### Post by Ranko Kohime on 2013-08-10
Get the processor cooking by using the [prime95]("http://www.mersenne.org/freesoft/") torture test.  The processor will get hotter than the motherboard almost certainly.

---

### Post by abrake on 2013-08-11
> **Ranko Kohime said:**
> Get the processor cooking by using the [prime95]("http://www.mersenne.org/freesoft/") torture test.  The processor will get hotter than the motherboard almost certainly.

That's a great idea! After running mprime for about 20 minutes the temperatures stabilized at 70°C and 64°C. temp1 shot up as soon as I started mprime which leads me to believe that it's the cpu temperature, whereas temp2 rose slowly:
[ATTACH=CONFIG]245268[/ATTACH]

I've been digging around a bit more, and I've found from two different sources ([here]("http://www.legitreviews.com/article/2047/18/") and [here]("http://www.guru3d.com/articles_pages/amd_a10_5800k_review_apu,8.html")) that it is possible to monitor the individual core temperatures on the AMD 5800k, at least with windows software. That makes me wonder (1) how is my cpu temperature related to the individual core temps (e.g. is it just the mean of all four or is it a different sensor entirely?), and (2) how can I find the core temps on ubunutu.

---

