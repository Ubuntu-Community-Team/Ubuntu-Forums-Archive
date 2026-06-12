---
title: "Can open source amd drivers display gpu temperature?"
date: 2012-07-29
forum: Hardware
---

### Post by azurehoney on 2012-07-29
sensors command gives me this:

```

radeon-pci-0100
Adapter: PCI adapter
temp1:        +69.0°C  
```


Unfortunately it is wrong, the real temperature should be around 50 degrees Celcius. This can be confirmed with quick reboot to windows. So I would like to know if perhaps drivers themselves can show gpu temperature?


edit: this is real temperature and it is worrying

---

### Post by Laiquendi on 2012-07-29
It works properly on mine and I have open source drivers on ati too.
19C difference while booting is possible, maybe the card is just getting hot on your linux?

---

### Post by pqwoerituytrueiwoq on 2012-07-29
are you sure that is your GPU, and not the CPU
```
~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +30.5°C  (high = +70.0°C, crit = +90.0°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +0.92 V  (min =  +0.85 V, max =  +1.70 V)
 +3.3 Voltage:       +3.47 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.11 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.36 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:       898 RPM  (min =  600 RPM)
CHASSIS FAN Speed:  1352 RPM  (min =  600 RPM)
CHASSIS FAN 2 Speed:1278 RPM  (min =  600 RPM)
CPU Temperature:     +33.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:      +30.0°C  (high = +45.0°C, crit = +75.0°C)  


```My GPU is 32C according to my driver sensors does not even show a 32C

---

### Post by azurehoney on 2012-07-29
> **Laiquendi said:**
> It works properly on mine and I have open source drivers on ati too.
19C difference while booting is possible, maybe the card is just getting hot on your linux?


Yes you are right, I didn't know that temp can drop so fast! Fortunately I found a workaround

```
sudo sh -c "echo low > /sys/class/drm/card0/device/power_profile"
```
Will drop gpu temp below 50 degrees:
```
radeon-pci-0100
Adapter: PCI adapter
temp1:        +48.0°C
```

```
    sudo sh -c "cat /sys/class/drm/card0/device/power_profile"
    low

    sudo sh -c "cat /sys/kernel/debug/dri/0/radeon_pm_info"
    default engine clock: 900000 kHz
    current engine clock: 99990 kHz
    default memory clock: 1050000 kHz
    current memory clock: 150000 kHz
    voltage: 950 mV
```


Is ```
sudo sh -c "echo low > /sys/class/drm/card0/device/power_profile"
``` permanent? Or will it be reset after reboot?

---

### Post by pqwoerituytrueiwoq on 2012-07-29
use your [FONT=Courier New]/etc/rc.local[/FONT] file
```
echo low > /sys/class/drm/card0/device/power_profile
```added it on a new line before exit
nice find
will be trying this on my dads apu system

---

### Post by azurehoney on 2012-07-29
> **pqwoerituytrueiwoq said:**
> use your [FONT=Courier New]/etc/rc.local[/FONT] file

[I prefer this way]("http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/")


alt-f2:

```
gksudo gedit /etc/init.d/ati-power-save
```


write this in ati-power-save file:

```

#!/bin/sh
 
# ATI power save
echo profile > /sys/class/drm/card0/device/power_method
echo low > /sys/class/drm/card0/device/power_profile
```


save and run these commands:

```

sudo chmod +x /etc/init.d/ati-power-save 
sudo update-rc.d ati-power-save defaults 99
```

So far I had one hang after resume from suspend.

---

### Post by azurehoney on 2012-07-30
And another hang, this is too much for me :( Back to proprietary drivers.

---

### Post by brainwash on 2012-07-30
How about switching to dynamic power management? Definitely worth a try.
```
echo dynpm > /sys/class/drm/card0/device/power_method
```

---

