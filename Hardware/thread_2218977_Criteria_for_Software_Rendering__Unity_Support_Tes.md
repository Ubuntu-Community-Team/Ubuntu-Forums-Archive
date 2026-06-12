---
title: "Criteria for Software Rendering?  Unity_Support_Test"
date: 2014-04-22
forum: Hardware
---

### Post by KAWill70 on 2014-04-22
I recently ran the Unity Support Test located in /usr/lib/nux/ on Ubuntu 14.04.

As shown below, my system has software rendering which makes things run extremely slow.  Does anyone know the criteria that triggers software rendering?  Would a motherboard based graphics controller with limited memory be one reason?

Note also that Unity 3D is not being supported.

```
kent@kent-desktop:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
	Subsystem: Gigabyte Technology Co., Ltd SiS661FX GUI 2D/3D Accelerator

kent@kent-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.0

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
kent@kent-desktop:~$
```

---

### Post by grahammechanical on 2014-04-22
It could be that the electronics in the graphic adapter are not capable of doing rendering so it has to be done by software. Don't you think? The graphics card cannot do 3D rendering.

---

### Post by Yellow Pasque on 2014-04-22
> The graphics card cannot do 3D rendering. 
No, the hardware is capable of 3D acceleration, but not under Linux. There were some attempts at 3D Linux drivers for SiS GPU's, but they never panned out.

Basically, OP should probably abandon Unity and run a lighter desktop (like xfce or lxde).

---

### Post by KAWill70 on 2014-04-23
Temujin - Thanks very much for the reply.  The thread referenced below passes along the good news that SIS Graphics are now being supported in Ubuntu 14.04 and its variants.

However, the information you passed along suggests that those drivers only support 2D meaning that the Unity Desktop in Ubuntu 14.04 is not supported for SIS Video Cards.  That is unfortunate.  I wonder if there is any hope that 3D drivers for SIS Graphics might eventually become available.

[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by Yellow Pasque on 2014-04-23
Don't hold your breath for 3D SiS drivers. It's probably not happening.
There is zero support/documentation/code from SiS itself and there's probably not enough interest in reverse-engineering.

---

