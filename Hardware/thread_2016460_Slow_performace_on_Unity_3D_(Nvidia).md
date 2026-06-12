---
title: "Slow performace on Unity 3D (Nvidia)"
date: 2012-07-04
forum: Hardware
---

### Post by mahela007 on 2012-07-04
I have an Nvidia card and because of all the problems with the normal driver in the repos, I installed the 302.17 driver from the Ubuntu-X ppa. 

However, Unity 3D seems to be a bit slow: 
The launcher takes a relatively long time to open (about a second or two)
Moving windows about increases CPU usage quite a bit. 
Glxgears provides good frame rates (59 - 60) but the movement of the gears seems rough.. (it looks much smoother when I run glxgears on from Unity 2D) 

What could be the problem?

This is what "system test" showed. 
graphics/compiz_checkPASSEDOpenGL vendor string:   NVIDIA Corporation OpenGL renderer string: GeForce 7100 / nForce 630i/integrated/SSE2 OpenGL version string:  2.1.2 NVIDIA 302.17  Not software rendered:    yes Not blacklisted:          yes GLX fbconfig:             yes GLX texture from pixmap:  yes GL npot or rect textures: yes  Compiz supported:         yes

---

