---
title: "support for ATI Radeon IGP 345 M chipset"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by RoD on 2004-12-01
I've read in this thread ([http://www.ubuntuforums.org/showthread.php?t=2404](http://www.ubuntuforums.org/showthread.php?t=2404)) that probably 3D acceleration would work properly with the Radeon IGP 345 M chipset (mine is working in a compaq presario 25xx laptop), but glxgears shows that it doesn't works properly. I paste the test results:
---------------------------------------------------------------------------------------------------
$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1161 frames in 5.0 seconds = 232.200 FPS
1808 frames in 5.0 seconds = 361.600 FPS
1808 frames in 5.0 seconds = 361.600 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1243 frames in 5.0 seconds = 248.600 FPS
1243 frames in 5.0 seconds = 248.600 FPS
1130 frames in 5.0 seconds = 226.000 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1130 frames in 5.0 seconds = 226.000 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1017 frames in 5.0 seconds = 203.400 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1017 frames in 5.0 seconds = 203.400 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1130 frames in 5.0 seconds = 226.000 FPS
1243 frames in 5.0 seconds = 248.600 FPS
1017 frames in 5.0 seconds = 203.400 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1017 frames in 5.0 seconds = 203.400 FPS
1243 frames in 5.0 seconds = 248.600 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1808 frames in 5.0 seconds = 361.600 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1808 frames in 5.0 seconds = 361.600 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1808 frames in 5.0 seconds = 361.600 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1582 frames in 5.0 seconds = 316.400 FPS
--------------------------------------------------------------------------------------

I've tried to install the fglrx-driver but it doesn't work for my chipset. What can I do to get 3D acceleration?

---

