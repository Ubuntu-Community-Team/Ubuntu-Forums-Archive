---
title: "Memtest86 v1.70 Errors"
date: 2008-08-23
forum: Hardware
---

### Post by newbuntuxx on 2008-08-23
hey guys...

i got a another pc on which I installed ubuntu. For the past two weeks, whenever i am playing nexuiz or watching a movie, after 30-45 mins, the pc freezes and makes a very loud noise through the speakers. I have to force a cold shut down by holding the power button for 10 seconds.

at first i thought it was a heat problem with my 8800 GT. So, I manually adjusted the fan speed to run at 100% at all times. But the pc continued to crash.

At last, I decided to check the memory, and voila!

I got 22 erros at 153.1mb and 153.3. The total amount of mem that I have is 2048mb.

As you can see, the errors are at the beginning of the stick. So, my question is: How can I fix these errors? if they are fixable that is.

Any suggestions, links, etc... will be helpful.

thanks guys

---

### Post by molochi on 2008-08-23
You could slow the memory down and/or increase the the SPD timings. Both are bios setup settings. I'll assume you know how to find them as it looks like your system is running at a custom clock speed, if not tell us your motherboard mfg/model. If you are running DDR2-800 I'd try 6-6-6-18 timings first and run memtest again for a while. If that doesn't do it drop the memory speed setting a notch. 

If you are running well under the specified frequency of your memory (say you got ddr2-800 and you keep getting errors running at ddr2-667 speeds) you may just have a bad dimm.

---

### Post by newbuntuxx on 2008-08-25
here is my system info:

```
Processor(s)	 
Number of processors	1
Number of cores	2 per processor
Number of threads	2 per processor
Name	AMD Athlon 64 X2 4400+
Code Name	Brisbane
Specification	AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
Package	Socket AM2 (940)
Family/Model/Stepping	F.B.2
Extended Family/Model	F.6B
Brand ID	4
Core Stepping	BH-G2
Technology	65 nm
Core Speed	2300.0 MHz
Multiplier x Bus speed	11.5 x 200.0 MHz
HT Link speed	1000.0 MHz
Stock frequency	2300 MHz
Instruction sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64
L1 Data cache (per processor)	2 x 64 KBytes, 2-way set associative, 64-byte line size
L1 Instruction cache (per processor)	2 x 64 KBytes, 2-way set associative, 64-byte line size
L2 cache (per processor)	2 x 512 KBytes, 16-way set associative, 64-byte line size
Chipset & Memory	 
Northbridge	ATI RS690/RS690M rev. 00
Southbridge	ATI SB600 rev. 00
Graphic Interface	PCI-Express
PCI-E Link Width	x16
PCI-E Max Link Width	x16
Memory Type	DDR2
Memory Size	2048 MBytes
Memory Frequency	328.6 MHz (CPU/7)
CAS# Latency (tCL)	5.0 clocks
RAS# to CAS# (tRCD)	5 clocks
RAS# Precharge (tRP)	5 clocks
Cycle Time (tRAS)	15 clocks
Bank Cycle Time (tRC)	21 clocks
Command Rate (CR)	1T
System	 
System Manufacturer	System manufacturer
System Name	System Product Name
System S/N	System Serial Number
Mainboard Vendor	ASUSTeK Computer INC.
Mainboard Model	M2A-VM
BIOS Vendor	Phoenix Technologies, LTD
BIOS Version	ASUS M2A-VM ACPI BIOS Revision 1404
BIOS Date	10/09/2007
Memory SPD	 
Module 1	DDR2, PC2-5300 (333 MHz), 2048 MBytes, PDP Systems
```

when i bought the computer i resetted the bios settings to defaults, so, i dont think the system has any custom speeds. However, i dont know for sure, so please direct me.

thanks

---

### Post by molochi on 2008-08-26
Well your memory timings and speed look stock there, though memtest was reporting a higher speed. Unfortunately your motherboard (Asus m2a-vm) doesn't appear to support custom timings in bios setup. You can manually set the memory speed to 533/pc4200 according to the manual. so you could try that, just to see if the errors go away. However, I'd also get the memory replaced since 1) it is failing while running in-spec 2) you'll experience some performance hit (not a lot mind you) and 3) the problem could reappear if a chip is going bad.

You can DL the manual here [http://dlsvr04.asus.com/pub/ASUS/mb/socketAM2/M2A-VM/e3088_m2a-vm.pdf](http://dlsvr04.asus.com/pub/ASUS/mb/socketAM2/M2A-VM/e3088_m2a-vm.pdf). Navigating bios is explained starting on page 55 (2-11) and the relevant settings are on page 66 (2-22).

Quick and dirty version (may not be acurate as I'm just RTFM)
Press <Del> during POST to bring up Bios Setup. 
Use the l/r arrow key to move to Advanced
Use the up/down arrow key to get to DRAM Configuration
Change Timing Mode auto to manual
Go down to Memory Clock Frequency
Change Auto to DDR2 533

Press f10 to save the changes

Run memtest again. Good Luck.

---

