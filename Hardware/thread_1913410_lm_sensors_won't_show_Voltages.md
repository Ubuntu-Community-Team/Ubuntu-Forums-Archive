---
title: "lm_sensors: won't show Voltages"
date: 2012-01-22
forum: Hardware
---

### Post by Lockheed on 2012-01-22
I am running thinkpad R61 on C2D and there is no way I can force lm sensors to show me voltages. I know adding acpi_enforce_resources=lax to grub, but it doesn't change a thing (I would not be surprised if it was just being ignored, just as the 'quiet' option is, making the boot process littered with useless verbose messages).

Here's the output:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +79.0C  (crit = +127.0C)
temp2:        +75.0C  (crit = +100.0C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3117 RPM
temp1:        +79.0C  
temp2:        +43.0C  
temp3:        +35.0C  
temp4:        +68.0C  
temp5:        +50.0C  
temp6:            N/A  
temp7:        +28.0C  
temp8:            N/A  
temp9:        +41.0C  
temp10:       +48.0C  
temp11:       +54.0C  
temp12:           N/A  
temp13:           N/A  
temp14:           N/A  
temp15:           N/A  
temp16:           N/A  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +69.0C  (high = +105.0C, crit = +105.0C)
Core 1:       +75.0C  (high = +105.0C, crit = +105.0C)
```

---

