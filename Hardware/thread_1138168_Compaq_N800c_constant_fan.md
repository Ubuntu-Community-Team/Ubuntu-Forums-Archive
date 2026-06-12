---
title: "Compaq N800c constant fan"
date: 2009-04-26
forum: Hardware
---

### Post by rhy7s on 2009-04-26
Have installed Ubuntu Studio 9.04 with the real time kernel. The fan never quits, it's not on full but still does my head in. In XP the fan only comes on rarely and corresponds to load. Have installed lm-sensors and added acpi_osi="Linux" to grub's menu.lst. 'sensors-detect' finds no sensors, 'sensors' output is:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C  (crit = +93.0°C)                  
temp2:       +42.0°C  (crit = +93.0°C)                  
temp3:       +16.0°C  (crit = +93.0°C) 
```
Which should be fine for a laptop, though I do notice idle CPU usage seems a bit higher than XP - idling at about 15% with occasional spikes to about 35%. Processor scaling seems to be working fine. Any suggestions on what other terms I should be searching for to try and resolve this?

---

### Post by rhy7s on 2009-05-03
After updates in the past few days CPU usage seems to have dropped a bit, idling at about 10%, spiking to 30%. Fan still incessant.

---

