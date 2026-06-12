---
title: "Mobile Intel® 4 Series Express Chipset Family"
date: 2010-04-10
forum: Hardware
---

### Post by 1Michael1 on 2010-04-10
Hi I've got the laptop (HP ProBook 4510s) which works all good running XP which the laptop was provided with.
But I'd rather prefer running Ubuntu on it as main (Running dual-boot right now) but the only problem I got is the driver for Mobile Intel® 4 Series Express Chipset Family that I can't seem to find for Linux (Ubuntu). I've been looking around like a maniac on Intels site without any succes. I've tried running the Windows drivers through Wine (Yeah pretty stupid, tho better testing than not).

So if anyone know a way to get the chipset to work properly on Ubuntu I'd truly truly appreciate the effort and the help. Because as for now, my laptop is very limited due to the lack of chipset.

Thanks in advance and I hope you could help me out,
Michael.

---

### Post by emanuel.b on 2010-04-10
Limited? How So?

---

### Post by 1Michael1 on 2010-04-10
Because I'm working with OpenGL and as for now, I'm barely able to run it.

So anyone able to help?

---

### Post by emanuel.b on 2010-04-10
It may be your graphics card. I guess you're running an Intel grapics chipset, correct?

---

### Post by 1Michael1 on 2010-04-10
Yeah as said, got Mobile Intel® 4 Series Express Chipset Family.

---

### Post by emanuel.b on 2010-04-10
> Hi I've got the laptop (HP ProBook 4510s) which works all good running XP which the laptop was provided with.
But I'd rather prefer running Ubuntu on it as main (Running dual-boot right now) but the only problem I got is the driver for Mobile Intel® 4 Series Express Chipset Family that I can't seem to find for Linux (Ubuntu). I've been looking around like a maniac on Intels site without any succes. I've tried running the Windows drivers through Wine (Yeah pretty stupid, tho better testing than not).

Oh, I thought you were referring to the CPU. ](*,)

Anyway, In my experience, Intel Express chipsets never really run OpenGL that well. But still, have you checked the "System -> Administration -> Hardware Drivers"?

---

### Post by 1Michael1 on 2010-04-10
No proprietary drivers are in use on this system.

---

### Post by emanuel.b on 2010-04-10
Well, I guess you're stuck with the Open Source drivers. Well, if you're running 9.10, you could wait for 10.04, which comes out at the end of the month, and see if it any better then...

---

### Post by 1Michael1 on 2010-04-11
Yeah, so what if it doesn't work at 10.04?
Ain't there some other way?

---

### Post by cascade9 on 2010-04-11
The drivers for the intel chipsets are built into the kernel as far as I know. You dont have to add the drivers with linux liek you do with windows. Same goes for the intel video drivers. 

> In general, many Linux* distributions already include Intel® graphics drivers. If you are looking to update your driver, Intel recommends checking on availability and obtaining precompiled driver packages from your Linux distribution vendor or computer manufacturer. Support for these drivers will be through your Linux distribution vendor or computer manufacturer.

[http://www.intel.com/support/graphics/sb/CS-010512.htm](http://www.intel.com/support/graphics/sb/CS-010512.htm)

There are ways of increasing performance with them from what I know, but I cant be sure about that- I dont use intel chipset graphics at all. I would search here for your intel graphics (probably "Extreme Graphics 2") and maybe at intelgraphics.org-

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

---

### Post by AfterCrash on 2010-10-25
Same issue here. P-Lease help... lol. I'm sure you pro's get tired of hearing this :( I have a chipset:

Mobile Intel 4 series Express Chipset Family. 

I am fairly computer savy.

I have recently converted from windows to Ubuntu. My version is 10.10. I am also a mild gamer. None of that crazy stuff. But I cant get OpenArena or QuakeLive to run smoothly. In fact OpenArena just freezes after 3 or 4 min's of play. I can hear my self running around but the VIDEO is dead/forzen in place. I cant even exit the program. I have to do a Hard Boot. I can do most anyhting.. watch movie/music/flash. But when it comes to more 3d stuff it crashes. I could DO all this in windows, and the games I play are OLD so I have no compatibility issues. I think it may concern my driver. I have yet to find a driver for my INTEL chipset that's for ubuntu/Linux. 

IF ANYONE CAN PLEASE HELP I'M DROWNING IN SORROW AND MISERY :guitar:
- Brandon

---

### Post by listerdl on 2011-05-03
i might have the same thing as you...

did you solve this - i.e. can you upgrade our Mobile Intel(R) 4 Series Express Chipset Family chipset?

thanks

---

### Post by srf21c on 2011-06-01
Same issue on an HP Elitebook 6930p.   Apparently there are two graphics Intel display chips available. Ubuntu 11.04 recognizes both but only configures one of them w/the i915 driver.  Take a look at the output from "sudo lshw" command:

```
*-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=[COLOR="Red"]i915[/COLOR] latency=0
             resources: irq:46 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:7138(size=8)
        *-display:1 [COLOR="#ff0000"]UNCLAIMED[/COLOR]
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0400000-d04fffff
```


I rebooted into Windows XP to confirm, and sure enough in Device Manager there are two instances of the display driver. 

Right now the maximum screen resolution that I can set is 1024x768.  I want to crank this up to the native 1680x1050 resolution of the attached HP L2208w monitor.

Hoping that this thread will provide me with the info needed: [[COLOR="Blue"]Intel Mobile 4 Chipset - i915 - Change resolution[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1629950")

---

### Post by ivotkl on 2012-11-30
Hello. I need to update my graphic drivers (Mesa I think as it is from December 2009 XD - before date of purchase of my computer actually hahaha). Well, back to my point. I can' t use Intel LD website cause some part of it might conflict with the game I' m trying to run.

```

$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:
```

Hope you can help.

By doing a small research I could not find so far how to update them. I' ll go deeper into mesa' s website and let you know. But, if you can post a solution while I'm at work so I can work out a solution when I come back. Thanks in advanced!

---

### Post by gdiasamidze on 2013-01-20
[http://askubuntu.com/questions/73074/intel-hd-graphics-card-not-recognized-in-system-info](http://askubuntu.com/questions/73074/intel-hd-graphics-card-not-recognized-in-system-info)

---

