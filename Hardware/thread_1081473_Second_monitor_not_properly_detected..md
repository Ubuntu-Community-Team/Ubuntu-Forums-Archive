---
title: "Second monitor not properly detected."
date: 2009-02-26
forum: Hardware
---

### Post by DragonRagnarok on 2009-02-26
I have two Acer AL1717 monitors. One is about a year newer. nvidia-settings properly detects the older one, but the newer one is listed as CRT-1 instead of AL1717, and I only have a limited choice of resolutions to pick from.

It sounds to me like the monitor is not properly identifying itself, but if that's the case, I don't know what I to do to fix it.

---

### Post by nixscripter on 2009-02-27
Plug in the monitor, and then run this in a Terminal to see what it thinks it is: ```
xrandr -q
```

---

### Post by DragonRagnarok on 2009-02-27
```
Screen 0: minimum 320 x 240, current 2432 x 1024, maximum 2432 x 1024
default connected 2432x1024+0+0 0mm x 0mm
   1280x1024      50.0     51.0     86.0  
   1280x960       52.0     53.0     54.0  
   1152x864       55.0     56.0     57.0     58.0     59.0  
   1024x768       60.0     61.0     62.0     63.0  
   960x600        64.0  
   960x540        65.0  
   840x525        66.0     67.0     68.0  
   832x624        69.0  
   800x600        70.0     71.0     72.0     73.0  
   720x450        74.0  
   700x525        75.0  
   680x384        76.0     77.0  
   640x480        78.0     79.0     80.0  
   512x384        81.0     82.0  
   400x300        83.0  
   320x240        84.0     85.0  
   2432x1024      86.0* 
```

Currently running twinview. Left monitor is at 1280x1024, right monitor (the troublesome one) is 1152x864 (the max I can set it to)

---

### Post by nixscripter on 2009-03-01
Is that all the output there is? There should also be a screen 1 listed below it. That looks like the first screen (which is working).

---

