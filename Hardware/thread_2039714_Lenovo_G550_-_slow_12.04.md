---
title: "Lenovo G550 - slow 12.04"
date: 2012-08-09
forum: Hardware
---

### Post by Niorko on 2012-08-09
My machine is **Lenovo G550** with **Intel GMA4500**

Every new version of Ubuntu and maby sometimes when I have time I came to Ubuntu and give it a try. But every time I meet with problems. When I'd installed Ubuntu, I feel that everything is slow and a little bit sluggish. 


----------


My friend have tried me help and told me, that I shoud try this things:

```
$ glxinfo | grep direct
$ glxinfo | grep OpenGL
```

Results: 

```
$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
```

```
$ glxinfo | grep direct
direct rendering: Yes
```


And with: `glxgears` I got 60fps thanks to vsync no more for sure...


----------


But on the other side, maby I am spoiled with Windows 8... I don't think so. Opening nautilus for the first time is slow, Unity Dash last 2sec to open. Opening Chrome and FF is slow too. On the Chrome, there is no MapsGL support. One more th**ing, I can post is this:

**Graphics Feature Status**

 - Canvas: Software only, hardware acceleration unavailable
 - Compositing: Software only, hardware acceleration unavailable 
 - 3D CSS: Unavailable. Hardware acceleration unavailable 
 - CSS Animation: Software only, hardware acceleration unavailable 
 - WebGL: Unavailable. Hardware acceleration unavailable 
 - WebGL multisampling: Unavailable. Hardware acceleration unavailable
 - Flash 3D: Unavailable. Hardware acceleration unavailable 
 - Flash Stage3D: Unavailable. Hardware acceleration unavailable

**Problems Detected**

 - Intel mesa drivers are crash-prone.: 76703
 - Accelerated 2d canvas is unstable in Linux at the moment.
 - Stage3D is not supported on Linux.: 129848

**Version Information**

 - Data exported	Thu Aug 09 2012 10:55:52 GMT+0200 (CEST)
 - Chrome version	21.0.1180.75 (Oficiálne zostavenie 150248)
 - Operating system	Linux 3.2.0-27-generic-pae
 - Software rendering list version	1.45
 - ANGLE revision	1046
 - 2D graphics backend	Skia


----------

I really want to use Ubuntu for my daily use and helps it to improve and maby later write some program for its. I think, that Ubuntu has big potential, but these thing make me crazy. Could someone help me, please? =)

PS: Unity2D works like that...

---

### Post by Niorko on 2012-08-09
Last problem with Chrome MapsGL I solved by enabling some features in ```
about:flags
```, but fps on 3D google map is significantly worse then on Windows.

---

