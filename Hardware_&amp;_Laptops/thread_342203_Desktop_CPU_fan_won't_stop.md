---
title: "Desktop CPU fan won't stop"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by PeteNJ on 2007-01-19
So I just got a new machine E6400, ASrock 945G Mobo. I installed Edgy and no matter what the CPU fan won't stop. I checked in the BIOS and it says it should turn off if the processor is less than 50 degrees C. I was worried so I downloaded a CPU Temp monitor and it is running at a reasonable 28 degrees. 

The noise is driving me nuts. Any advice?

---

### Post by david_2001 on 2007-01-20
The fan won't stop but the motherboard should be running it at low speed if the processor temperature is below the preset threshold.  My ASrock 775Dual-VSTA / Pentium D 820 is quiet when the processor isn't busy - browsing, playing a CD/DVD - but the cpu fan roars up to full speed when both processor cores are working hard.  The next step for me will be to replace the standard Intel cpu cooler with something bigger that has a 120mm fan.  (I've already got a large case lined with sound absorbing foam, quiet power supply and 120mm intake/exhaust fans.)

---

### Post by PeteNJ on 2007-01-20
It isn't though. No matter what I do it runs at over 3,500 rpm even when it is idle and I am not running any other applications. And that is after I changed the BIOS setting to run the fan on slow. I have never had a computer run so loudly.

---

### Post by david_2001 on 2007-01-20
Hmmm.  If it were me having this problem then I'd take the following steps, in order, checking after each step whether the problem has gone away rather than doing everything at once:

[LIST=1]
[*]Confirm that "CPU Quiet Fan" is enabled in the BIOS settings and that the threshold temperature is reasonable.
[*]Power down, open the case and check that the cpu fan header is plugged into the cpu fan connector on the motherboard (CPU_FAN1, or however it might be labelled).  I would also confirm that the header is 4 pin and that it is properly seated on the motherboard connector.
[*]Check the manufacturer's website for an upgraded BIOS.  If there is then update the BIOS, making sure to keep a copy of the original if I can.
[/LIST]
If all of the above failed and I had another suitable cpu fan then I'd try it, just to eliminate the original as being the problem.  Otherwise, I'd be sending it all back for repair/exchange.

---

### Post by tweedledee on 2007-01-21
I've had mixed success (in multiple O/S's) with BIOS control of the fan, and personally prefer to do it all "manually" via software in the O/S.  Take a look at this thread for an approach that works to keep my computer much quieter: [http://www.ubuntuforums.org/showthread.php?t=42737](http://www.ubuntuforums.org/showthread.php?t=42737).

---

### Post by david_2001 on 2007-01-22
Two points of view.  I prefer not to have to tinker too much, so I've tried to make my PC quiet by design.  The inlet/exhaust case fans are 1,100rpm 17db 120mm items, though I'm presently using the Intel cooler with 92mm fan that came with the Pentium D 820.  The cpu fan will max out at 2,400rpm but normally spins at 1,100rpm and the whole plot is barely audible from a couple of yards away.  Here's the output of sensors, grabbed as I'm writing this:

> w83697hf-isa-0290
Adapter: ISA adapter
...
Case Fan: 1004 RPM  (min =  799 RPM, div = 8 )                     
CPU Fan:  1110 RPM  (min =  799 RPM, div = 8 )                     
M/B Temp:    +35°C  (high =   +45°C, hyst =   +40°C)   sensor = thermistor           
CPU Temp:  +40.0°C  (high =   +50°C, hyst =   +45°C)   sensor = thermistor

---

### Post by wh0rd on 2007-01-25
I have the same issue. When my Ubuntu is in idle the cpu jumps up and all the fans turn on full speed, then when I resume from idle mode it goes back down and fan reduces. I don't think it's the hardware or bios. It has something to do with Ubuntu for sure. 

Btw I'm on:
Ubuntu Edgy Eft (kernel 2.6.17-10-generic)
Pentium 4 HT

---

### Post by wh0rd on 2007-01-25
Apparently it's beagle making the trouble. I removed it and the system is running normal. There seems to be a bug:
[https://launchpad.net/ubuntu/+source/beagle/+bug/64326](https://launchpad.net/ubuntu/+source/beagle/+bug/64326)

---

