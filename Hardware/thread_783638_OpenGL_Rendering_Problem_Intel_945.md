---
title: "OpenGL Rendering Problem Intel 945"
date: 2008-05-05
forum: Hardware
---

### Post by jcabraham on 2008-05-05
I'm having trouble running a game. The significant error seems to be:
 
pbuffer creation error:  glXChooseFBConfig() failed

I'm running Hardy latest on a Dell Latitude 620, Intel 945 graphics chip. Driver is xserver-xorg-video-intel2:2.2.1-1ubuntu12 (latest). I have libgl1-mesa-dri and libgl1-mesa-glx installed. Compiz works great, 

glxinfo says:
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

But the info the game is retrieving is:
Mon May  5 22:43:07 2008 [info]: OpenGL vendor string: Tungsten Graphics, Inc
Mon May  5 22:43:07 2008 [info]: OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
Mon May  5 22:43:07 2008 [info]: OpenGL version string: 1.3 Mesa 7.0.3-rc2

Any ideas? It seems hard to debug...

---

