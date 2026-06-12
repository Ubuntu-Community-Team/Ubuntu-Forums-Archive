---
title: "xsensors - are there any controls?"
date: 2010-01-31
forum: Hardware
---

### Post by momist on 2010-01-31
Hi there,

I'm running Karmic Koala on AMD64, for the first time, having upgraded from 32 bit PC2100 ancient hardware.  The processor is an old AMD X2 3800+ 2GHz, on an Asus A8V MoBo.

Being worried about the health of my new (somewhat expensive) processor, I installed xsensors, and with some help from the archives here, I managed to find the "sudo sensors-detect" command, and the necessary reboot (my son tells me that re-boots are _never_ necessary in Linux) and "Lo and Behold" xsensors works . . .  after a fashion.  

However - my dual core processor can tell me about the temperature of each core, as revealed by the CLI "sensors" command - see code - but the graphical display only reveals core 0.  xsensors says to me -12V is only 6v, as does "sensors" in the command line.  The BIOS version doesn't agree, about any of these "ALARM" figures. I'm certain that the machine wouldn't work properly if any of these were true.  And anyway, the "Minimum" is higher than the "Maximum"!

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +44.0°C                                    
Core1 Temp:  +46.0°C                                    

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.31 V  (min =  +0.00 V, max =  +3.84 V)   
+12V:       +11.67 V  (min = +14.47 V, max = +14.35 V)   ALARM
+3.3V:       +3.34 V  (min =  +3.76 V, max =  +3.44 V)   ALARM
+5V:         +5.15 V  (min =  +4.56 V, max =  +6.69 V)   
-12V:        +6.06 V  (min =  +5.90 V, max =  -3.64 V)   ALARM
V5SB:        +5.13 V  (min =  +6.18 V, max =  +0.99 V)   ALARM
VBat:        +3.23 V  (min =  +4.05 V, max =  +3.95 V)   ALARM
fan1:          0 RPM  (min = 10150 RPM, div = 1)  ALARM
CPU Fan:    1383 RPM  (min = 8653 RPM, div = 4)  ALARM
fan3:       1394 RPM  (min = 7670 RPM, div = 8)  ALARM
M/B Temp:    +28.0°C  (high = +63.0°C, hyst = -80.0°C)  sensor = thermistor
CPU Temp:    +42.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       +26.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.475 V
beep_enable:enabled
```

Is there a guide to editing the config file so that xsensors tells the truth?

Thanks for any guidance.

Ian

---

