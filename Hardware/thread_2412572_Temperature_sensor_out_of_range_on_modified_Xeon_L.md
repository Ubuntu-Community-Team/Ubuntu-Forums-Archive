---
title: "Temperature sensor out of range on modified Xeon L5420"
date: 2019-02-14
forum: Hardware
---

### Post by conan1981 on 2019-02-14
Hello, 

im using the latest 64 bit Xubuntu (fully updated) on a HP3010 small form factor pc.
i have replaced the original 2.7Ghz Dualcore Pentium cpu with an
modified Xeon l5420 2.5ghz quadcore  (sticker mod). cpu is running perfect, bios detects cpu correct, and system
is really fast, however the cpu fan is running at full speed.

I think the output from temp2 (sensor output below)  is missread, that, or my 8 euro cpu from Aliexpress is
broken :)

i tried severall fancontrol tuturials to "reroute" the sensor connected to fan1 to another, like temp
1 or 3, unfortunatly i keep failing.

does anyone have a suggestion?

sensors output:
```

                        f8000-isa-0a00
 Adapter: ISA adapter
 +3.3V:        +3.41 V   
 3VSB:         +3.36 V   
 Vbat:         +3.28 V   

 **fan1:        6276 RPM**

 fan2:           0 RPM  ALARM

 fan3:           0 RPM  ALARM
 fan4:           0 RPM
 temp1:        +30.0°C  (high = +70.0°C, hyst = +60.0°C)
 **temp2:       +228.0°C  (high = +100.0°C, hyst = +85.0°C)  ALARM**

 temp3:        +28.0°C  (high = +100.0°C, hyst = +85.0°C)
 
 
 nouveau-pci-0400
 Adapter: PCI adapter
 GPU core:     +0.95 V  (min =  +0.95 V, max =  +1.14 V)
 fan1:        1500 RPM
 temp1:        +25.0°C  (high = +95.0°C, hyst =  +3.0°C)
                        (crit = +105.0°C, hyst =  +5.0°C)
                        (emerg = +135.0°C, hyst =  +5.0°C)
 
 
 coretemp-isa-0000
 Adapter: ISA adapter
 Core 0:       +37.0°C  (high = +73.0°C, crit = +85.0°C)
 Core 1:       +35.0°C  (high = +73.0°C, crit = +85.0°C)
 Core 2:       +37.0°C  (high = +73.0°C, crit = +85.0°C)
 Core 3:       +38.0°C  (high = +73.0°C, crit = +85.0°C)
```

---

### Post by Yellow Pasque on 2019-02-16
What does the temperature and fan speed read in the BIOS?

---

### Post by conan1981 on 2019-02-16
Thanks for your reply,

The ami bios on this systeem is extremely primitive (looks like an 486 bios), no fan control or speed/temperature readout....

---

### Post by conan1981 on 2019-02-16
Fan speed is low, almost silent during bios checks, als soon as Xubuntu boots, fan spins up to full speed.

---

