---
title: "Opengl games lockup my Computer"
date: 2011-07-05
forum: Hardware
---

### Post by Ekeluo on 2011-07-05
I have an Intel Pentium T2370 laptop (Compaq A900) with GMA X3100 (GM965) graphics, running **Kubuntu** Natty. Basically, some games run fine and others don't. The 1st couple I installed (Battle for wesnoth & Warzone 2100) work alright (though Warzone almost always causes X to crash on exit), but neverball/putt, speed-dreams & Astromenace don't. Starting them just locks up the computer (noaudio or visual reaction) and the screen turns black after 2 seconds. Power button still causes complete shutdown. Speed-dreams and astromenace (the very same packages from get-deb.net) work on my **Ubuntu ** maverick install on the same laptop.

Standing by for any required info ( Have about 2 or 3 hrs). Any help will be appreciated as this problem is holding me from fully moving to natty.

---

### Post by Ekeluo on 2011-07-10
Anyone? Please?

---

### Post by notte on 2011-07-12
I've noticed the same behaviour trying to run google earth and some other opengl apps fullscreen. I see elsewere people have similar issues.

These are my specs:

```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)

client glx vendor string: Mesa Project and SGI
client glx version string: 1.4

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20

glxinfo | grep -i direct
direct rendering: Yes
```

Bug really similar:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760322](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760322)

Hope that someone jumps here with a solution or even an idea!  ;)

---

