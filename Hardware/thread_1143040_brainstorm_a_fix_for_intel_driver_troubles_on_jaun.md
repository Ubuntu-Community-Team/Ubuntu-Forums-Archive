---
title: "brainstorm a fix for intel driver troubles on jaunty"
date: 2009-04-29
forum: Hardware
---

### Post by tschew on 2009-04-29
I want to create a movement for fixing the 2.6 intel driver situation on jaunty until a new version will implement UXA without GEM (for old hardware / old kernels) or the EXA performance regression is fixed in the driver.

Keith Packard explains what has changed with the intel driver: [http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/]("http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/")

So far, there appear to be a number of possible fixes for poor graphics performance:

modern chipsets - 
1) enable uxa, hope for stability
2) fix the mtrr ranges and continue to use exa

old chipsets -
3) fix the mtrr ranges and continue to use exa
4) switch back to the 2.4 driver

I wonder whether one could use the jockey system to implement these things.

1) We would need to list which chipsets work reliably with UXA right now, and simply switch it on via some script.

2) / 3) Fixing the MTRR range is step 4 in this guide: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582") It does not require the installation of the experimental kernel. (thanks to zack evans for clarifying this)

It should be easy to automate via a script and can then be introduced into xinit or so. I will fumble around with sed/awk/grep/echo a bit and should have an automated script which will read the correct memory ranges and sizes and set up write-combining in two or three days. 

4) revert to 2.4: [http://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("http://ubuntuforums.org/showthread.php?t=1130582") - this improves performance but is far from ideal

What does everyone else think?

-Bartek

---

### Post by Kareeser on 2009-04-29
Hmmm...

I have an i855, one of the cards affected by the new driver. I tried setting MTRR ranges in an attempt to get flash playback to work properly, to no avail, but now I'm wondering whether this might fix my other issues related to video problems as well.

I shall reluctantly give it a try, seeing as it took me about an hour to figure out the proper MTRR ranges to use for my card!

Edit:
Test 1: Properly set MTRR ranges for my card. Ran xrandr. Laptop hard locked. Alt-SysReq-REISUB did nothing. :(
Test 2: Same as above. I give up for now. Unless I'm setting up the values wrong, but there's no error message saying I did it wrong.

```
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03ef00000 ( 1007MB), size=    1MB, count=1: uncachable
reg02: base=0x03f000000 ( 1008MB), size=   16MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  128MB, count=1: write-combining

00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
	Subsystem: Dell Device [1028:018d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb


```

---

### Post by tschew on 2009-04-30
@Kareeser: Thank you for the information. I remember someone mentioning that write combining doesn't work at all on the 855, but I'm not sure if I'm remembering correctly...

Your MTRR range setting looks just like on my systems so I think it should be correct.

---

### Post by tschew on 2009-04-30
I've run a few benchmarks using different configurations on two chipsets (G35 and i915), trying EXA, UXA, with MTRR, without MTRR, with optimizations (greedy), without and all EXA combinations on the 2.4 driver.

I've also written an automated version of the fixmtrr.sh script which extracts the ranges, gets them into the correct format and send sets them.

Both the benchmarks and the script can be found here: [https://www.hackerspace.lu/wiki/Tracking_intel_performance_regression](https://www.hackerspace.lu/wiki/Tracking_intel_performance_regression)

---

