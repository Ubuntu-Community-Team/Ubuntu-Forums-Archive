---
title: "Problem with monitor resolution on Ubuntu 12.04 LTS"
date: 2014-02-19
forum: Hardware
---

### Post by giuseppemaxpugliese on 2014-02-19
The monitor resolution is not modifiable in my Ubuntu 12.04 LTS distribution. I have already checked in various forums, trying to install the original drivers and not, but I did not find the solution to my problem ](*,).

I queried the system, for installed video cards, the result is the following:```
spci -nnk | grep -iA2 VGA


01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS780 [Radeon HD 3200] [1002:9610] Subsystem: Acer Incorporated [ALI] Device [1025:014e] Kernel modules: radeon
--
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] [1002:954f] Subsystem: PC Partner Limited / Sapphire Technology Device [174b:e990] Kernel modules: radeon
``` 
The monitor is connected to the second device (Radeon HD 4350/4550). Have you any solution? :confused:

---

