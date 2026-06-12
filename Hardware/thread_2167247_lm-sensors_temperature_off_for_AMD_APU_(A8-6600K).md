---
title: "lm-sensors temperature off for AMD APU (A8-6600K)"
date: 2013-08-13
forum: Hardware
---

### Post by Ranko Kohime on 2013-08-13
CPU: AMD A8-6600K APU
MB: ASUS F2A85-M/CSM

The output of lm-sensors, (and to be fair, Core Temp when running in Windows as well), is significantly off.  It reports idle temperatures that drop to near freezing levels, (with a larger-than-stock air cooler), and only puts out the correct temperature (or what I surmise to be correct), when the CPU is under enough load to get it up to 45-50°C.

On Windows, as I mentioned, Core Temp experiences the same issue, however a program that ASUS provides for their board, AI Suite, seems to register the correct temperatures, with idle temps in the 30's and full load temps peaking over 50°C.

Is anyone aware of a solution to make lm-sensors read correctly?

---

### Post by Colin_OFlynn on 2013-09-25
Did you have any luck?

I see two adapters which should be reading the core temps on my AMD APU, but have clearly wrong temps:
```

Adapter: PCI adapter
temp1:         +7.1°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

radeon-pci-0008
Adapter: PCI adapter
temp1:         +7.0°C  
```

As you mention under load they look somewhat more reasonable, but based on my BIOS readings are clearly still too low:

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +31.1°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +19.0°C 

```
There's also a few other temperature readings from the MB:
```

temp1:        +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:         -8.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +45.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI

```
The temp1 seems to be MB temperature sensor, and temp3 looks like it 'could' be the core temp. But it's still lower than reported via the BIOS system, so something odd is happening...

---

### Post by Colin_OFlynn on 2013-09-25
BTW just as a follow-up: it looks like the readings in k10temp etc are always going to be garbage. From the AMD BIOS & Kernel Developers Guide:

```

2.10.1 The Tctl Temperature Scale
Tctl is the processor temperature control value, used by the platform to control cooling systems. Tctl is accessible
through SB-TSI and F3xA4[CurTmp]. Tctl is a non-physical temperature on an arbitrary scale measured in
degrees. It does not represent an actual physical temperature like die or case temperature. Instead, it specifies
the processor temperature relative to the point at which the system must supply the maximum cooling for the
processor&#8217;s specified maximum case temperature and maximum thermal power dissipation. It is defined as follows
for all parts:
&#8226; For Tctl = 0 to Tctl_max - 0.125: the temperature of the part is [Tctl_max - Tctl] degrees under the temperature
for which maximum cooling is required.
&#8226; For Tctl = Tctl_max to 255.875: the temperature of the part is [Tctl - Tctl_max] degrees over the worst-case
expected temperature under normal conditions. The processor may take corrective actions that affects performance
or operation as a result, such as invoking HTC or THERMTRIP_L.

```

---

