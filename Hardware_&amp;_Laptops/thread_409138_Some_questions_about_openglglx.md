---
title: "Some questions about opengl/glx"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by muzzz on 2007-04-14
I'm trying to optimize my 3D experience on a laptop that's "blessed" with an Intel 855 graphics card. Unfortunately I know very little about properly configuring OpenGL under Linux. Performance was absolutely horribly at first, but things seem to have improved a little after I enabled AIGLX as part of installing Beryl.

I'm now left with three main questions:

1) Is there any way to tell exactly what graphics driver I'm using? I'm guessing it's the driver contained in xserver-xorg-video-i810 package, since it's the only thing I can find relating to intel and video. But I'd like to make sure, as a starting point to search for better drivers.

2) When looking at the glxinfo output I see fivedifferent version strings:

```
$ glxinfo | grep version

libGL warning: 3D driver claims to not support visual 0x4b
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 1.3 Mesa 6.5.1
glu version: 1.3
```

Can anyone tell me which version is used where, or how the different versions relate? Also, what version do I need to look at to see if my setup is compatible with a program that says it requires OpenGL 1.<something> support?

3) Are there any other packages / drivers / rendering infrastructures I should try?

I'm running Ubuntu/Kubuntu 6.10, but I'd also be interested in suggestions to try once Feisty is released.


Thanks in advance,

Daan

---

