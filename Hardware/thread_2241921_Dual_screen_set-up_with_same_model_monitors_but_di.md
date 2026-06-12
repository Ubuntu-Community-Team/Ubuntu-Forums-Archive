---
title: "Dual screen set-up with same model monitors but different resoulutions on 14.04"
date: 2014-08-29
forum: Hardware
---

### Post by MZ250Supa5 on 2014-08-29
I've just upgraded to 14.04 and I have this problem I have a twin Hanns G HW191D monitor setup and am using an Nvidia GeForce 210 graphics card to run the twin monitors. Using the Nvidia 331.38 driver Nvidia X Server Settings is reporting back to me that it recognises the one monitor correctly,(CRT-1) but not the first, (CRT-0).

 Monitor CRT-0 is connected using VGA and CRT-1 is connected using the DVI connector with a VGA adapter.  I know it's not an issue with the graphics card as I've also tried sedtting up the system using a GeForce GT640 with similar results.

Here is the xrandr output:

```
rhiannon@rhiannon:~$ xrandr
Screen 0: minimum 8 x 8, current 2464 x 900, maximum 8192 x 8192
DVI-I-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
VGA-0 connected 1440x900+1024+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     66.0     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     66.0     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
rhiannon@rhiannon:~$ 

```

This issue, which should really be a non-issue is really spoiling my day - had the monitors been of vastly different specs and manufacturers then perhaps a few difficulties could be anticipated, but  when both monitors are from the same manufacturer and of exactly the same specification then it should be trivial to set these monitors up - indeed, it should work 'out of the box' as it used to with 10.04. 

Is it really that strange that people commonly use dual screen configurations?

---

