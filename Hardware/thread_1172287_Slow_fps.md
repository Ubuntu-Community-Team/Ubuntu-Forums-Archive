---
title: "Slow fps"
date: 2009-05-28
forum: Hardware
---

### Post by diek85 on 2009-05-28
Hello everybody


I'm experiencing slow fps rate on my ThinkPad T60 (boarding an "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)" according to *lspci* command).

I noticed it using Stellarium: fps value stucks at 3/4 fps and the program is impossible to be used. Compiz *benchmark* plugin reports 30 frames/sec while *glxgears* reports

1800 frames in 5.0 seconds = 359.862 FPS
1858 frames in 5.0 seconds = 371.457 FPS
1853 frames in 5.0 seconds = 370.473 FPS
1848 frames in 5.0 seconds = 369.473 FPS
1834 frames in 5.0 seconds = 366.636 FPS

I've tried to follow this guide [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) as well as this [http://wiki.ubuntu-it.org/Hardware/Video/Intel/Jaunty](http://wiki.ubuntu-it.org/Hardware/Video/Intel/Jaunty) but the problem remains unsolved. My Xorg.0.log reports that DRI2 and UXA are currently active (the problem remains unsolved even if I use EXA instead of UXA). The ubuntu version currently installed is 9.04.

Am I missing something? Is there anyone who is expericing the same problem?

Thanks everybody 
Diego

---

