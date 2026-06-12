---
title: "Changing CPU available frequencies"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by raksasha on 2007-05-19
Hello,
I have a small problem with overclocking, I have Athlon 64 3000+ and Ubuntu 7.04.

When I've installed Ubuntu, the CPU's frequency was set to 2.0 GHz. Since that, the default CPU scaling available frequencies are 1.0, 1.8  and 2.0 GHz.
Lately, I've increased the CPU frequency in BIOS to 2.2Ghz. But it has no effect in Ubuntu when powernowd is running, because the scaling available frequencies are still the same. (I can see them in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies)

I think I'd need to change these values to solve my problem. (for example to 1.0, 1.8 and 2.2 GHz)
Would somebody know how to do that, please ?  Thank you !

---

### Post by smsmith050 on 2007-05-22
If your BIOS allows you to increase the CPU clock then all the frequencies derived from the CPU clock will increase. The core frequency, DDR, and HT frequencies will all increase. 
The BIOS builds a table of FID's and VID's for each performance state. 
 0 : fid 0xe (2200 MHz), vid 0xe
 1 : fid 0xc (2000 MHz), vid 0x10
 2 : fid 0xa (1800 MHz), vid 0x10
 3 : fid 0x2 (1000 MHz), vid 0x12
The driver uses this table to increase or decrease the performance as needed.  
So if you increase the input clock frequency then you also need to increase the voltage for each state. 
Normally the input clock is 200Mhz. So 5 x 200Mhz = 1000Mhz and so on. The voltage increases as the VID code decreases. 
You need a way to over-ride the normal performance state table and use your own. 
You might also need to increase the HT voltage and the DDR voltage since they are derived from the input clock.

---

