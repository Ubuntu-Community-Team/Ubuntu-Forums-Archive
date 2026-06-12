---
title: "3D really weak performance..yeah I did google.."
date: 2009-09-07
forum: Hardware
---

### Post by alinux-lb22 on 2009-09-07
Hi All

I did check out this great tutorial

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#How%20It%20Works](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#How%20It%20Works)

But I dont have any of the problems mentioned there.

As of my system info:


glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090326 2009Q1 RC2 x86/MMX/SSE2


glxgears
4644 frames in 5.0 seconds = 928.674 FPS
4930 frames in 5.0 seconds = 985.967 FPS
4866 frames in 5.0 seconds = 973.056 FPS
4968 frames in 5.0 seconds = 993.439 FPS
4688 frames in 5.0 seconds = 937.398 FPS


I am really not expecting super 3D performance, but my hardware is pretty new although it is "only" an Intel VGA it still got 256 MB RAM assigned to it. 
One thing I totally HATE, is that youtube videos flicker in full screen, and the same goes for movies.


I am NOT using compiz, Desktop effects or any fancy stuff. Since the performance of that stuff was bad and making my Ubuntu experience even worse.

My XORG file.

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

---

