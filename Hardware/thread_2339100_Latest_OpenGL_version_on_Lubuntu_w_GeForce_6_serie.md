---
title: "Latest OpenGL version on Lubuntu w/ GeForce 6 series"
date: 2016-10-04
forum: Hardware
---

### Post by explodinglem on 2016-10-04
I installed Lubuntu this week, and i want to install the latest OpenGL drivers, but all i seem to get is 1.4, according to the glxinfo command. I have a Nvidia 6150 SE graphics card.

Is there a way to get OpenGL 3.1 or better?

---

### Post by deadflowr on 2016-10-05
> Is there a way to get OpenGL 3.1 or better?
I don't think so, as that card should only have support up to OpenGL 2.1.

Anyway, what was the output from glxinfo the OpenGL version or the glx version? Which would indeed be 1.4.

And which graphics driver is in use?
I think you can get the legacy nvidia-304 driver to work with that card.

---

### Post by explodinglem on 2016-10-05
The glxinfo command outputs this:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

then this:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/integrated/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 304.131
OpenGL shading language version string: 1.20 NVIDIA

---

### Post by Yellow Pasque on 2016-10-05
There is a difference between the OpenGL version and the glx version.

There is nothing wrong with your output. You have the latest version of glx and OpenGL (relevant to your particular GPU).

---

