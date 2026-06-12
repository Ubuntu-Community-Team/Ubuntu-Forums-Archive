---
title: "ubuntu low gpu usage but really high cpu usage"
date: 2020-11-12
forum: Hardware
---

### Post by imjellythefish on 2020-11-12
So I switched over to ubuntu 20.04 a couple months ago, and since 1 week ago I'm getting really high cpu usage and really low gpu usage. This causes very low fps in pretty much every game. For example 20 fps on Minecraft and GTA V. Lowering the graphics doesn't change the fps.
  

My specs:

GPU: 980TI
CPU: I7-4790K
RAM: 16 GB DDR3
Motherboard: MSI Z97 PC Mate
SSD: 250GB
HDD: 1TB
Power Supply: 650W

---

### Post by CelticWarrior on 2020-11-12
Welcome.

> [COLOR=#000000]GPU: 980TI[/COLOR]

Have you installed the Nvidia proprietary drivers? Which version? Is Secure Boot disabled?

---

### Post by imjellythefish on 2020-11-12
I have the "NVIDIA driver metapackage from nvidia-driver450 (proprietary)" drivers installed, and secure Boot is disabled.

---

### Post by imjellythefish on 2020-11-12
I have a picture of my game cpu and gpu usage while the game was running, 1fps. :/
My also runs poorly for the first 5 minutes after closing the game.
[screenshot: https://ibb.co/gDCCF0T]("https://ibb.co/gDCCF0T")

---

### Post by Yellow Pasque on 2020-11-13
Can you show the output of:
```
glxinfo -B
```

---

### Post by imjellythefish on 2020-11-14
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 6144 MB
    Total available memory: 6144 MB
    Currently available dedicated video memory: 5714 MB
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 980 Ti/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 450.80.02
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6.0 NVIDIA 450.80.02
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)

OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 450.80.02
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

---

