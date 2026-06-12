---
title: "Enable 900Mhz P-State on AMD A8-4500M running Ubuntu 14.04"
date: 2016-07-20
forum: Hardware
---

### Post by suiciwd on 2016-07-20
I have undervolted my CPU using **TurionPowerControl** and it lowered the CPU temperature from **88[FONT=arial]°[/FONT]C** to **76[FONT=arial]°[/FONT]C**.Now I also need to reduce the idle temperature (I have already undervolted all my P-States and my idle is 50C. The room temperature is 28 - 33[FONT=arial]°[/FONT]C) so I think I would need to reduce the clock speed on idle. Here is the output of **sudo tpc -l**
```

TurionPowerControl 0.44-rc2+ (export) Linux 64-bit
Turion Power States Optimization and Control - by blackshard


Main processor is Family 15h (Bulldozer/Interlagos/Valencia) Processor
    Family: 0xf        Model: 0x0        Stepping: 0x1
    Extended Family: 0x15    Extended Model: 0x10
    Package Type: 0x1    BrandId: 0x0    
Machine has 1 nodes
Processor has 4 cores
Processor has 8 p-states
Processor has 2 boost states


Power States table:
-- Node: 0 Core 0
core 0 pstate 0 (pb0) - En:1 VID:52 FID:12 DID:0.00 Freq:2800 VCore:1.2250
core 0 pstate 1 (pb1) - En:1 VID:100 FID:7 DID:0.00 Freq:2300 VCore:0.9250
core 0 pstate 2 (p0) - En:1 VID:114 FID:3 DID:0.00 Freq:1900 VCore:0.8375
core 0 pstate 3 (p1) - En:1 VID:118 FID:2 DID:0.00 Freq:1800 VCore:0.8125
core 0 pstate 4 (p2) - En:1 VID:119 FID:1 DID:0.00 Freq:1700 VCore:0.8062
core 0 pstate 5 (p3) - En:1 VID:122 FID:16 DID:1.00 Freq:1600 VCore:0.7875
core 0 pstate 6 (p4) - En:1 VID:128 FID:12 DID:1.00 Freq:1400 VCore:0.7500
core 0 pstate 7 (p5) - En:0 VID:128 FID:2 DID:1.00 Freq:900 VCore:0.7500
-- Node: 0 Core 1
core 1 pstate 0 (pb0) - En:1 VID:52 FID:12 DID:0.00 Freq:2800 VCore:1.2250
core 1 pstate 1 (pb1) - En:1 VID:100 FID:7 DID:0.00 Freq:2300 VCore:0.9250
core 1 pstate 2 (p0) - En:1 VID:114 FID:3 DID:0.00 Freq:1900 VCore:0.8375
core 1 pstate 3 (p1) - En:1 VID:118 FID:2 DID:0.00 Freq:1800 VCore:0.8125
core 1 pstate 4 (p2) - En:1 VID:119 FID:1 DID:0.00 Freq:1700 VCore:0.8062
core 1 pstate 5 (p3) - En:1 VID:122 FID:16 DID:1.00 Freq:1600 VCore:0.7875
core 1 pstate 6 (p4) - En:1 VID:128 FID:12 DID:1.00 Freq:1400 VCore:0.7500
core 1 pstate 7 (p5) - En:0 VID:128 FID:2 DID:1.00 Freq:900 VCore:0.7500
-- Node: 0 Core 2
core 2 pstate 0 (pb0) - En:1 VID:52 FID:12 DID:0.00 Freq:2800 VCore:1.2250
core 2 pstate 1 (pb1) - En:1 VID:100 FID:7 DID:0.00 Freq:2300 VCore:0.9250
core 2 pstate 2 (p0) - En:1 VID:114 FID:3 DID:0.00 Freq:1900 VCore:0.8375
core 2 pstate 3 (p1) - En:1 VID:118 FID:2 DID:0.00 Freq:1800 VCore:0.8125
core 2 pstate 4 (p2) - En:1 VID:119 FID:1 DID:0.00 Freq:1700 VCore:0.8062
core 2 pstate 5 (p3) - En:1 VID:122 FID:16 DID:1.00 Freq:1600 VCore:0.7875
core 2 pstate 6 (p4) - En:1 VID:128 FID:12 DID:1.00 Freq:1400 VCore:0.7500
core 2 pstate 7 (p5) - En:0 VID:128 FID:2 DID:1.00 Freq:900 VCore:0.7500
-- Node: 0 Core 3
core 3 pstate 0 (pb0) - En:1 VID:52 FID:12 DID:0.00 Freq:2800 VCore:1.2250
core 3 pstate 1 (pb1) - En:1 VID:100 FID:7 DID:0.00 Freq:2300 VCore:0.9250
core 3 pstate 2 (p0) - En:1 VID:114 FID:3 DID:0.00 Freq:1900 VCore:0.8375
core 3 pstate 3 (p1) - En:1 VID:118 FID:2 DID:0.00 Freq:1800 VCore:0.8125
core 3 pstate 4 (p2) - En:1 VID:119 FID:1 DID:0.00 Freq:1700 VCore:0.8062
core 3 pstate 5 (p3) - En:1 VID:122 FID:16 DID:1.00 Freq:1600 VCore:0.7875
core 3 pstate 6 (p4) - En:1 VID:128 FID:12 DID:1.00 Freq:1400 VCore:0.7500
core 3 pstate 7 (p5) - En:0 VID:128 FID:2 DID:1.00 Freq:900 VCore:0.7500


 --- Node 0:
Processor Maximum PState: 7
Processor Startup PState: 5
Processor Maximum Operating Frequency: 2800 MHz


Minimum allowed VID: 184 (0.4000V) - Maximum allowed VID 52 (1.2250V)
Done.

```

As you can see I have undervolted my CPU but the 900Mhz is disabled (it was the same before undervolt).I tried enabling it with **sudo tpc -core all -en 7 **but it doesn't appear in CPUFreq Indicator and also** cpufreq-aperf **doesn't show it going to the 900Mhz freqency even with **Powersave **governer.So how can I enable it and use the P-State.

Laptop specs

Manufacturer : Hewlett Packard
Model : Pavilion g7 2269wm
CPU / APU : 1.9Ghz up to 2.8Ghz AMD Quad-Core A8-4500M Accelerated Processor
RAM : 6GB DDR3 SDRAM (2 DIMM user accessible)
GPU : AMD Radeon HD 7640G Discrete-Class graphics and up to 3060MB total graphics memory
Display : 17.3-inch diagonal HD+ BrightView LED-backlit display (1600 x 900)
Touchpad : Touchpad support multitouch gestures with on/off button

---

### Post by suiciwd on 2016-08-08
bump

---

### Post by mörgæs on 2016-08-08
Why do you use 14.04 and not 16.04?

---

### Post by Yellow Pasque on 2016-08-08
It seems you're not the only one with the issue: [http://www.tomshardware.com/answers/id-1873553/amd-4400m-lowest-state-undervolting.html](http://www.tomshardware.com/answers/id-1873553/amd-4400m-lowest-state-undervolting.html)

I have a laptop with with an AMD APU and I'll play around with TPC the next time I use it to see if it does the same thing for me.

> **mörgæs said:**
> Why do you use 14.04 and not 16.04?

It's the user's choice, right? LTS is not my cup of tea either, but do you have any reason to think this issue might be solved by a newer kernel?

---

### Post by mörgæs on 2016-08-09
Though I don't know the exact direction of kernel development I still believe that one should try the latest Buntu release when hardware support might be the problem.

---

### Post by suiciwd on 2016-11-03
I am now using elementary OS Loki (based on 16.04) and the issue is still there (also 16.04 introduced WiFI issues and no fglrx)

---

