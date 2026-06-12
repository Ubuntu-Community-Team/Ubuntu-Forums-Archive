---
title: "fan control on clevo P17SM-A"
date: 2015-11-21
forum: Hardware
---

### Post by H4F on 2015-11-21
My laptop Sager NP8278 - also known as Clevo P17SM-A and many others (eurocom, xmg, system76, bonobo)

**Issue:** Fan never stops completely even if the temperature 
```
h4f@h4f:/proc/acpi$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  (crit = +120.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +46.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:         +43.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:         +42.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:         +41.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:         +44.0°C  (high = +84.0°C, crit = +100.0°C)

```
[B]
Possible solution[/B] I found that on windows there is a tool [HWInfo]("http://www.hwinfo.com/forum/Thread-Solved-Monitor-CPU-and-GPU-fan-RPM-on-Clevo-laptops?pid=4519#pid4519") that can control fan speed on clevo laptops. Getting into more details revealed:
 
```
[SIZE=2][FONT=Arial Narrow]For example, on a P170HM, the status of the fan RPM data is reported in the Embedded Controller I/O space (EC_SC/EC_DATA=0066/0062) at the following byte offsets:
CPU Fan: D0 D1
GPU Fan: D2 D3

The DxDy is a 16-bit word that reports the tick counts (N_ticks) of the EC clock per fan revolution. The RPM value can be obtained by:
Fan_RPM = (32768 * 60) / N_ticks

Typical values of fan speed readings in these registers:

CPU Fan: 00 00 ==> 0 RPM
03 20 ==> 2457 RPM
01 FA ==> 3885 RPM

GPU Fan: 00 00 ==> 0 RPM
03 52 ==> 2313 RPM
02 1E ==> 3627 RPM[/FONT][/SIZE]

```

My question is how I can write and read from those addresses?

---

### Post by qonqon on 2016-11-04
Pretty old thread, but anyway:
I have found out the same adresses for the fan speed and some additional one:
- 0xCE shows CPU fan duty cycle
- 0xCF shows GPU fan duty cycle if Windows is bootet with Hotkey utility. Somehow this is not exposed when I run Linux. Could not find out why yet.
- 0x07 exposes CPU temperature

Fan duty cycle can be set as well with port 01 controlling cpu fan speed and port 02 controlling gpu fan speed.
This allows to pin the fans to a certain duty cycle, but you cannot program a fan curve.
I have not found out how set to set one of the automatic modes (automatic / overclock).
I have modified a tool that I found on github to do this: [https://github.com/davidrohr/clevo-indicator/network](https://github.com/davidrohr/clevo-indicator/network)

I would be really eager to find out:
- How to query GPU temperature and current GPU fan duty cycle.
- How to activate one of the automatic fan modes.
- Whether it is possible to reprogram the fan curves.

---

