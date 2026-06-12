---
title: "NVIDIA GeForce 6200 PCI card -- blacklist"
date: 2011-05-28
forum: Hardware
---

### Post by topofmurrayhill on 2011-05-28
I've installed Ubuntu 11.04 onto an old Dell to use as a development system and also added an EVGA GeForce 6200 PCI card because the system only has PCI slots. I just want to augment the graphics hardware enough to try out the Unity desktop, get respectable video performance, etc. Nothing fancy.

I'm using the driver from the nvidia-current package, set up xorg.conf for nvidia and everything seems to be configured correctly, but I'm still logging into the classic desktop. According to compiz-check there's a blacklist issue. Here is some other relevant output (see arrow):

$ /usr/lib/nux/unity_support_test -p

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6200/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06


 Not software rendered:    yes
Not blacklisted:          no     <---------
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

 Unity supported:          no

I wonder if this is expected. I wouldn't think a GeForce 6200 card would pose a problem. There's an entry in /etc/modprobe.d/blacklist-framebuffer.conf for "nvidiafb" and otherwise all I found was blacklist entries for nvidia drivers earlier than the current one.

---

### Post by topofmurrayhill on 2011-05-29
I think this is a spurious compatibility issue in this instance. I resolved it by adding UNITY_FORCE_START=1 to /etc/environment. That allows Unity to run and everything seems to be fine.

---

