---
title: "HDMI : Vague, genenric newbie question"
date: 2017-04-19
forum: Hardware
---

### Post by nickTaylor1181 on 2017-04-19
HI all


I've just acquired this little mini-projector (AAXA P700)... running it from a Ubuntu Studio laptop... 


Is HDMI always worse quality than files displayed from a USB stick?


Anything displayed via HDMI looks a bit like it's running 256 colours or something  - bad quality. Exactly the same files put onto a USB stick are a whole lot better. As you'd expect in fact.


So that was question 1.


If the answer to that is "no".... question 2 is : does anyone have any idea how I can improve the quality? 

Ubuntu Studio etc. I'm not sure what to supply by way of supporting information. I'm a bit out of my depth here.





Nick

---

### Post by mastablasta on 2017-04-19
wow that is really vague. 

HDMI is HD output on GPU, so it's quality should be HD. how well it shows on projector depends on projectors abilities, it's settings and the settings on the output device.

as for where to start - it's here: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

at the minimum people will need GPU model, any drivers you may have installed for it, Ubuntu version and your HDMI output settings (resolution on HDMI output, colours etc.)

---

### Post by Autodave on 2017-04-19
Also make sure that your cable is good.  First generation HDMI cables were not very good.....and cheap ones were worse. Some only support up to 720 resolution. Try a known good cable: its a lot easier than playing in the terminal. :-)

---

### Post by nickTaylor1181 on 2017-04-20
Hiya - thanks for getting back to me.

I've been through 4 HDMI cables now... the last was specifically advertised as being 1080p, so probably is.


I've been playing with this for the last couple of hours... hard to pin down exactly what is wrong... it's almost like anti-aliasing isn't working, although some of the colour-interpretation is way off as well.


Below are details of laptop, version of ubuntu, and output from driver/config-finding commands.

Is there anything else that might be useful?


....


The details of this laptop:

Ubuntu Studio 16.04
XFce 4.12

If I plug HDMI in, it says 

FTF40" 1920x1080



xrandr shows
..........................
```
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.06*+  59.93    40.04  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
HDMI1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 886mm x 498mm
   1920x1080     60.00*+  50.00    59.94    30.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02  
   1280x720      60.00    50.00    30.00    59.94    29.97    24.00    23.98  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



```




lspci | grep VGA
..........................
```
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
```





sudo lshw -c video
..........................
```
   *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:125 memory:b1000000-b1ffffff memory:a0000000-afffffff ioport:4000(size=64)



```

---

### Post by Autodave on 2017-04-20
Have you tried the projector on another machine?

---

### Post by Autodave on 2017-04-20
1,280 x 800 seems to be the max resolution of that projector: is that what you are outputting your video to it?

---

