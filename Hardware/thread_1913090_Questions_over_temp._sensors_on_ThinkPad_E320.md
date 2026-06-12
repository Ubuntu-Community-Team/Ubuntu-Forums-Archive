---
title: "Questions over temp. sensors on ThinkPad E320"
date: 2012-01-21
forum: Hardware
---

### Post by Hekla on 2012-01-21
To begin with, I was looking at why my battery discharge under Ubuntu was around twice that of under Windows, even though I am running Ubuntu on a SSD. Although it could be CPU use, through using PowerTOP on Ubuntu, I realised that my fan was using 7-8Watts.

When looking at l sensor measurements for temperature, I get the following:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  (crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:         828 RPM
temp1:        +44.0°C  
temp2:         +0.0°C  
temp3:        +41.0°C  
temp4:         +3.0°C  
temp5:         +0.0°C  
temp6:        +56.0°C  
temp7:        +28.0°C  
temp8:        +56.0°C  

I would like to know what the various temperatures refer to as I suspect the fan is running to cool the ones showing 56°C. Under Windows, hardware sensors don't show anything similar whilst idling.

I'm suspect that help here will require knowledge of the temperature sensors in my laptop, a ThinkPad Edge E320, but if there is anything else that could be suggested I would be thankful for it.

EDIT: Unusually my fan just stopped with no obvious change in the sensor measurement. So a) I would like to know what the measurements refer to, but more generally b) a better method of fan control. Would thinkfan do any good?

---

