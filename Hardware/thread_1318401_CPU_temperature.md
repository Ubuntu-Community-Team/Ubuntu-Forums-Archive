---
title: "CPU temperature"
date: 2009-11-07
forum: Hardware
---

### Post by flylehe on 2009-11-07
Hi

I have some questions concerning CPU temperature.

1. My laptop shuts itself down, which I guess is due to high CPU temperature. I want to confirm this by looking at some system log file that records the reason that the system shuts itself down. Is there any such syslog file? Where is it stored?

2. Also I have installed libsensors, which gives me different temperatures 
> 
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +97.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +57.0°C 

What do "acpitz-virtual-0" and "k8temp-pci-00c3" mean? As well as the meaning of "temp1" and "Core0 Temp"? Are the two temperatures both CPU temperatures?

How about the meaning of the temperature given by 
```

acpi -t

```
? Is it another different measure of CPU temperature?

3. I also wonder what you will do if the CPU temperature is exceeding some limit that you find is dangerous? I have also installed Computer Temperature Monitor (computertemp), which allows me to set up a limit temperature for alarm as well as command to execute when the limit is reached. So what command will you issue or things will you do when the temperature is exceeding the set limit to protect your laptop, instead of letting it shuts itself down?

Thanks and regards!

---

