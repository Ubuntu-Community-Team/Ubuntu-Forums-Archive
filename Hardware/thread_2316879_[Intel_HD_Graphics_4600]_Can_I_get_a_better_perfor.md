---
title: "[Intel HD Graphics 4600] Can I get a better performance?"
date: 2016-03-11
forum: Hardware
---

### Post by spawn2k99 on 2016-03-11
Hi there!

I'm using the **GPU** included in my **CPU** **Intel i5-4460**
I know from the Intel website that the **GPU** is [B]Intel HD Graphics 4600

[/B]I've heard in several occasions that 3D hardware acceleration is better than the software one.

1) May I know which one I have?

I can give the following information about my computer.

$ inxi -CGc0

CPU:    Quad core Intel Core i5-4460 (-MCP-) cache: 6144 KB 
           clock speeds: max: 3400 MHz 1: 3374 MHz 2: 3180 MHz 3: 1900 MHz 4: 2509 MHz

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1680x1050@60.0hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop GLX Version: 3.0 Mesa 10.1.3

2) is there any way to improve the 3D performance?

3) is there any way to test the performance? some benchmark maybe? I've heard that glxgears is not really a good benchmark.

Thanks in advance.

---

### Post by ajgreeny on 2016-03-11
That CPU does have Intel® HD Graphics 4600, as you thought.

I have no idea about benchmarking the graphics performance, I'm afraid, but you are correct that glxgears is not useful for that.

There is a package for 14.04 called **ubuntu-benchmark-tools** which may help, but I have never used it and I am not sure if it is worth using.

---

### Post by helgacecil on 2016-03-11
Mine:
$ inxi -CGc0
CPU:       Quad core Intel Core i5-4430 (-MCP-) cache: 6144 KB 
           clock speeds: max: 3200 MHz 1: 3147 MHz 2: 2559 MHz 3: 3199 MHz
           4: 3163 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.18.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x1024@85.02hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 11.1.2

[SIZE=2][FONT=arial]
For hardware acceleration you have to install the **i965-va-driver **,maybe it is already.With [/FONT][/SIZE]**vainfo **you can see if the card detects the acceleration.
Sorry, I don't know any benchmarking program.

---

### Post by goofprog on 2016-03-11
I don't understand the problem because ubuntu usually uses hardware acceleration drivers for the video devices now.  This includes nvidia.  The drivers may not be the vendor's drivers but they work.  It is not a great 3d device but as a guess I think intel makes that graphics system capable to use system memory as video ram.  I could be wrong but it is a classic hardware thing with intel graphics.

---

### Post by buzzingrobot on 2016-03-11
Yes, you have hardware acceleration with the Intel. 

Intel cooperates with the open source community and provides drivers for its GPU's.  The appropriate driver for your unit will be used by default. The only drivers come from Intel, they are used in every Linux distribution, and the odds are very slim that installing a different version of an Intel driver will change performance in any noticeable way.  Changing to a desktop environment that uses a different window manager -- Compiz vs Mutter vs KWin, etc. -- will, I think, be more likely to alter performance, up or down, in a way you might notice.

Intel video cannot compete with the video performance of high-end video cards from AMD and Nvidia. It isn't intended to do that. On the other hand, it comes with your CPU, it's a lot quieter and cooler, and you won't have to worry about it not working sometime after a kernel upgrade.

---

### Post by Yellow Pasque on 2016-03-12
> **spawn2k99 said:**
> I've heard in several occasions that 3D hardware acceleration is better than the software one. May I know which one I have?

This line indicates you have hardware acceleration working:
```
GLX Renderer: Mesa DRI Intel Haswell Desktop GLX Version: 3.0 Mesa 10.1.3
```

>  is there any way to improve the 3D performance?
Newer versions of Ubuntu bring newer drivers that may help a bit in performance. Other than that, there's no magic way to significantly improve performance.

---

### Post by Yellow Pasque on 2016-03-12
> **helgacecil said:**
> For hardware acceleration you have to install the **i965-va-driver **,maybe it is already.With [/FONT][/SIZE]**vainfo **you can see if the card detects the acceleration.

That's video decode acceleration as opposed to 3D acceleration.

---

### Post by efflandt on 2016-03-12
My gaming laptop has both Intel HD 4600 and Nvidia graphics and when comparing them on the same laptop, besides a noticeable difference in speed (and power use/heat generated) there were some benchmarks that would not even run on the Intel graphics because it was missing some features of more advanced graphics. Although, things have improved. Not sure if it was due to bumblebee for the dual hybrid graphics at that time, but in Ubuntu 13.10 Team Fortress 2 was unplayable with the Intel graphics, it would run very slowly and audio would repeat in short loops, but it is playable in Ubuntu 14.04 which has nvidia-prime to discretely run one graphics or the other.

If that is a desktop, one graphics card which could give you better graphics without using much power or without requiring a power supply upgrade is Nvidia GTX 750 or GTX 750 Ti. It was the first of the new generation with efficient Maxwell chip and most cards do not even have any auxiliary power connection because it is hardware regulated to 60 watts max which the PCI express bus should be able to supply (from 75 watt spec). With that, my whole PC only uses 150 watts AC input (measured with Kill A Watt meter). Although, if you have enough power the GTX 950 uses 90 watts or GTX 960 uses 120 watts.

---

### Post by spawn2k99 on 2016-03-12
Thank you all

---

