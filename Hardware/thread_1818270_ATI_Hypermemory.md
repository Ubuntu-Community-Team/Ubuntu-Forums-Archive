---
title: "ATI Hypermemory"
date: 2011-08-04
forum: Hardware
---

### Post by McBurto on 2011-08-04
Hello all,

I have a laptop with an ATI Mobility Radeon HD4250 integrated video card and would like to run Unity. I cannot run Unity because the video ram size is 256mb and Unity requires a minimum of 512mb. This used to be an easy fix - go into the bios and adjust the video ram size to make use of some of the 8192mb system ram. Unfortunately the laptop has **insidious **- whoops - that should be InsydeH20 bios and does not allow the shared ( or hypermemory ) to be adjusted. I am running the fglrx driver and have not been able to find anything in the driver settings, under the Catalyst control center or in the Ubuntu settings to change the size of video ram. ATI/AMD support has not been of any help, Compaq has not responded to any of my emails and InsydeH20 does not offer support for end users.
I also have to think that there are a lot of other users who may be in the same predicament.
My question - is there anything else I can do or am I stuck?

Thanks

---

### Post by .... on 2011-08-04
The requirement for Unity is 128MB video RAM: [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)
Run the unity GPU test:
```
sudo ./usr/lib/nux/unity_support_test -p
```
Of course, there's also Unity 2D if you still can't get the 3D running.

---

### Post by McBurto on 2011-08-04
Thanks for the reply.

I have run the test from the live CD and this is what I get:
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

Looks like it should work but every time I have tried to load it so far, it defaulted to the classic desktop. 

(And yes - the 3d unity desktop is active from the live CD.)

Is there something the live CD does/does not do that the install does regarding the display?

---

