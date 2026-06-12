---
title: "Fan control - HP DV3-4000sb"
date: 2010-09-17
forum: Hardware
---

### Post by sGroggy on 2010-09-17
Hi,

I've recently bought this laptop and so far I'm satisfied with it, however, the fan keeps running all the time and I do not seem to be able to do anything about it.

When runnings 'sensors' it returns:

```
groggy@groggy-laptop:/$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +58.0°C  (crit = +120.0°C)                  
temp2:       +47.0°C  (crit = +127.0°C)                  
temp3:       +54.0°C  (crit = +127.0°C)                  

```

Note that at the time I was writing this, the laptop was plugged in and charging, so the temperatures are higher than normal.


Running 'sensors-detect' finds nothing except for:

```
"Trying family `National Semiconductor'...                   Yes"

and

"Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS."

```
However, when I 'modprobe coretemp', 'sensors' returns:
```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +58.0°C  (crit = +120.0°C)                  
temp2:       +47.0°C  (crit = +127.0°C)                  
temp3:       +56.0°C  (crit = +127.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +57.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +54.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +59.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +53.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +57.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +53.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +59.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +54.0°C  (high = +84.0°C, crit = +100.0°C)  

```

But this doesn't help me any further of course...


Next I tried 'echo 3 > /proc/acpi/fan/FAN0/state' but cat shows me that the fan is still enabled, so the echo has absolutely no effect.

'dmesg | grep fan' returns the following:
```
[    1.868071] fan PNP0C0B:00: registered as cooling_device0

```

So I checked /sys/bus/acpi/devices/PNP0C0B:00 but I cannot find anything wrong.

Oh I also checked the BIOS, "FAN always on" seemed to be enabled, but disabling this also had no effect.



I hope someone who's a little bit brighter than me can shed some light on this issue :)


Best regards

---

