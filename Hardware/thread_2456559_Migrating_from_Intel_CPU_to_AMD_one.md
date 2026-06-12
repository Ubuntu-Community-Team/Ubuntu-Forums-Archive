---
title: "Migrating from Intel CPU to AMD one"
date: 2021-01-14
forum: Hardware
---

### Post by bsquare on 2021-01-14
My OS is currently Ubuntu 20.01 LTS.
 My current CPU is: Intel(R) Core(TM) i7-6700K CPU
 I'm going to upgrade my Motherboard, CPU, Memory, to AMD Family with an AMD Ryzen 9 5950x.
 Will my OS seamlessly work after hardware upgrade, or do I need to  perform some operation to upgrade my OS/Software to be able to work with  my new Hardware?

---

### Post by CelticWarrior on 2021-01-14
Backing up your personal files and reinstalling guarantees optimal results.
That the old installation will boot correctly in the new motherboard is not a given, especially when *not* installed in the proper UEFI mode (it should be for both the old and the new but many people inadvertently and often knowingly for reason that escape me still install in Legacy/CSM/"BIOS" mode).

---

### Post by TheFu on 2021-01-14
You want to disable any proprietary hardware drivers before the move. That is usually GPU and/or HW-RAID HBA drivers. Perhaps a NIC driver, but usually not.  The CPU will be discovered.  Oh, and becae that CPU is so bleeding edge, yo probably need the latest kernel available.  Do a little google research - probably need 5.8.x at least, maybe 5.10.x
[https://www.reddit.com/r/Amd/comments/joulqh/ryzen_5000_zen_3_linux_kernel_requirements/](https://www.reddit.com/r/Amd/comments/joulqh/ryzen_5000_zen_3_linux_kernel_requirements/)

---

### Post by bsquare on 2021-02-02
Thanks for your answers.
I prepared everything (+backup) to be able to reinstall everything.

It was a surprise, my Ubuntu boots up without any issue, without sofwtare reinstallation, after big Hardware upgrade.
Nevertheless, to avoid hasardeous behaviour in future, I performed a clean new installation taking back 100% of my nice nvme device :)
Everything works fine, despite of:
 - "EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)" error in logs (I read a 5.10 kernel is needed for that?).
 - still not having enough sensors feedback (my AMD CPU is not perfectly found, so I got a permanent 0°C report; and no fans feedbacks at all).
I tried lm-sensors, psensor, and even OpenHardwareMonitor.

May you advise me anything else?

---

### Post by QIII on 2021-02-02
If you have lm-sensors installed and have completed

```
sudo sensors-detect
```

would you please post the results of 

```
sensors
```


You may find that you are getting a CPU temp from the k10temp sensor.

---

### Post by mastablasta on 2021-02-02
> **bsquare said:**
> 
 - "EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)" error in logs (I read a 5.10 kernel is needed for that?).


makes sense. you have new hardware and for new HW, most up to date drivers will be in latest kernel.

**Option 1**
load 21.04 beta - but freeze will be at end of february: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)

**Option 2**
You could try just the new kernel.

install newer mainline kernel using Mainline: [https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/)
Mainline: [https://github.com/bkw777/mainline](https://github.com/bkw777/mainline)

or you can do it in CLI (manually): [https://itsfoss.com/upgrade-linux-kernel-ubuntu/](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)
[B]
Option 3[/B]
move to distro with new kernel implemented (maybe Manjaro, i think they just moved to 5.10)

---

### Post by kurt18947 on 2021-02-03
> **bsquare said:**
> Thanks for your answers.
I prepared everything (+backup) to be able to reinstall everything.

It was a surprise, my Ubuntu boots up without any issue, without sofwtare reinstallation, after big Hardware upgrade.
Nevertheless, to avoid hasardeous behaviour in future, I performed a clean new installation taking back 100% of my nice nvme device :)
Everything works fine, despite of:
 - "EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)" error in logs (I read a 5.10 kernel is needed for that?).
 - still not having enough sensors feedback (my AMD CPU is not perfectly found, so I got a permanent 0°C report; and no fans feedbacks at all).
I tried lm-sensors, psensor, and even OpenHardwareMonitor.

May you advise me anything else?

If you haven't done so, I'd install the latest BIOS update, or perhaps the 2nd to newest in case there are flaws lurking in the newest BIOS version. Doing so fixed a couple niggles on my 2nd gen Ryzen.

---

### Post by bsquare on 2021-02-03
> **mastablasta said:**
> makes sense. you have new hardware and for new HW, most up to date drivers will be in latest kernel.

**Option 1**
load 21.04 beta - but freeze will be at end of february: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)

**Option 2**
You could try just the new kernel.

install newer mainline kernel using Mainline: [https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/)
Mainline: [https://github.com/bkw777/mainline](https://github.com/bkw777/mainline)

or you can do it in CLI (manually): [https://itsfoss.com/upgrade-linux-kernel-ubuntu/](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)
[B]
Option 3[/B]
move to distro with new kernel implemented (maybe Manjaro, i think they just moved to 5.10)

Many thanks for all these information.
I prefer avoiding stability issue, so I'll stick on stock kernel provided with Ubuntu LTS Release 20.04.
Do you think kernel 5.10+ will be available as soon as it is regarded as stable enough, in this release?

---

### Post by bsquare on 2021-02-03
> **QIII said:**
> If you have lm-sensors installed and have completed

```
sudo sensors-detect
```

would you please post the results of 

```
sensors
```


You may find that you are getting a CPU temp from the k10temp sensor.
Yes it does, but always reporting 0°C (I guess because my kernel is """too old""").

But I've just tested the **acpi_enforce_resources=lax** kernel option which is great, and allows me to get everything I need (and more ^^).
Just not sure to what corresponds each name:
[HTML]hidpp_battery_0-hid-3-8
Adapter: HID adapter
in0:           3.98 V  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)

nvme-pci-0100
Adapter: PCI adapter
Composite:    +43.9°C  (low  = -273.1°C, high = +80.8°C)
                       (crit = +80.8°C)
Sensor 1:     +43.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +50.9°C  (low  = -273.1°C, high = +65261.8°C)

nct6798-isa-0290
Adapter: ISA adapter
in0:                      952.00 mV (min =  +0.00 V, max =  +1.74 V)
in1:                        1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                        3.34 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                      752.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                        1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                        3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                        3.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                      904.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                     232.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                     496.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                       1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                     1000.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                       1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                      831 RPM  (min =    0 RPM)
fan2:                      511 RPM  (min =    0 RPM)
fan3:                      786 RPM  (min =    0 RPM)
fan4:                        0 RPM  (min =    0 RPM)
fan5:                     2818 RPM  (min =    0 RPM)
fan6:                        0 RPM  (min =    0 RPM)
fan7:                      607 RPM  (min =    0 RPM)
SYSTIN:                    +39.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
CPUTIN:                    +37.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:                   +25.0°C    sensor = thermistor
AUXTIN1:                   +61.0°C    sensor = thermistor
AUXTIN2:                   +26.0°C    sensor = thermistor
AUXTIN3:                   +26.0°C    sensor = thermistor
PECI Agent 0 Calibration:  +38.0°C  
SMBUSMASTER 1:             +68.5°C  
PCH_CHIP_CPU_MAX_TEMP:      +0.0°C  
PCH_CHIP_TEMP:              +0.0°C  
intrusion0:               ALARM
intrusion1:               ALARM
beep_enable:              disabled

[/HTML]

---

### Post by bsquare on 2021-02-03
> **kurt18947 said:**
> If you haven't done so, I'd install the latest BIOS update, or perhaps the 2nd to newest in case there are flaws lurking in the newest BIOS version. Doing so fixed a couple niggles on my 2nd gen Ryzen.
Yes I did and I'm waiting for the next BIOS version, with crossfingers :)

---

