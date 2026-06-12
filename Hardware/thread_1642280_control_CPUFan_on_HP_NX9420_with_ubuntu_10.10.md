---
title: "control CPUFan on HP NX9420 with ubuntu 10.10"
date: 2010-12-10
forum: Hardware
---

### Post by vlad2005 on 2010-12-10
I have installed Ubuntu 10.10 on my HP NX9420. Everything work well, except that my laptop run noisy than in windows.
I try'it lm-sensors with sensors-detect, but seem that only temperature are reading, not cpu fan speed. I have installed cpufrequtils for cpu scalind and work well. My laptop it's clean.

Bellow it's my hardware:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
......................................

```
and cpu usage
```

CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.83 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.83 GHz:3.28%, 1.33 GHz:0.57%, 1000 MHz:96.15%  (3186)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.83 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.83 GHz:2.81%, 1.33 GHz:0.31%, 1000 MHz:96.88%  (2832)

```

 What can do to control cpu fan speed on this laptop?

---

### Post by vlad2005 on 2010-12-10
This is output from "sensors"
```
temp1:       +44.0°C  (crit = +256.0°C)                  
temp2:       +45.0°C  (crit = +102.0°C)                  
temp3:       +57.0°C  (crit = +110.0°C)                  
temp4:       +43.0°C  (crit = +105.0°C)                  
temp5:       +31.3°C  (crit = +102.0°C)                  
temp6:       +25.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +100.0°C, crit = +100.0°C) 
```

Temperature it's like when running windows.

---

