---
title: "Nvidia driver loading only after log out"
date: 2020-10-26
forum: Hardware
---

### Post by canhoto on 2020-10-26
Hi. 
I'm having this strange behavior in which my nvidia driver doesn't load when I first boot (or restart) the computer, but it does if I log out and log in again.
After booting, if I type ```
glxinfo | grep OpenGL
``` I have this:

> 
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 10.0.0, 128 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.1 Mesa 20.0.8
OpenGL shading language version string: 1.40
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:



After logging out from the session and logging in again, I have:
> OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 1050 Ti/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 450.66
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 450.66
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 450.66
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:



What can it be?

---

### Post by canhoto on 2020-10-28
Anyone?

---

