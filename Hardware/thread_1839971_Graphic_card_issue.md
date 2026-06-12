---
title: "Graphic card issue?"
date: 2011-09-06
forum: Hardware
---

### Post by layr on 2011-09-06
Not quite sure, but there seems to be kind of an issue with the GPU. Native 3D apps seem to work, tho some programs via Wine or VirtualBox (XP as guest) tend to be problematic.
Almost always it has something to do with OpenGL. For instance, 3D acceleration in VirtualBox enabled, running Sketchup gives error *"SketchUp was unable to initialize OpenGL! Please make sure you have installed the correct drivers for your graphics card. Error: ChoosePixelFormat failed"*

I'm not trying to get VirtualBox nor Wine support here, just a hint how to make sure whether the GPU is fully recognized and running.

Ubuntu 10.10
Quadro FX 570M
Various nVidia drivers, including the latest.

---

### Post by layr on 2011-09-16
*bring the post up*

---

### Post by BicyclerBoy on 2011-09-16
glxinfo | grep OpenGL
glxgears

---

### Post by 2F4U on 2011-09-17
You probably know that 3D support in Virtualbox is experimental, so I am not surprised that it doesn't work well. The next thing to consider is that Virtualbox "virtualizes" your graphics card too. That means that the Windows inside Virtualbox doesn't know that your card is nVidia Quadro FX 570M with all the capabilities.

---

### Post by layr on 2011-09-17
> **BicyclerBoy said:**
> glxinfo | grep OpenGL
glxgears
```
laur@laur-HP-Compaq-8510w:~$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Quadro FX 570M/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 280.13
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
```

glxgears run smoothly.

So the problem has to lay on the emulator and VM software side?

2F4U: okay. I actually thought ticking "3D acceleration" in VBox preferences allowed host to use the GPU directly.
I'll give other VM soft a try.

---

### Post by .... on 2011-09-17
You have to make sure the vbox guest additions are installed (in the guest) to get proper opengl support, or you will just get the vesa/non-accelerated driver.

---

### Post by layr on 2011-09-19
Vbox guest additions are installed.

---

### Post by .... on 2011-09-19
> **layr said:**
> Vbox guest additions are installed.
In XP, look in Device Manager under Dispaly Adapters. The adapter should be listed as VirtualBox Graphics Adapter and the Driver Provider should be Oracle Corp.

---

### Post by layr on 2011-09-19
> **.... said:**
> In XP, look in Device Manager under Dispaly Adapters. The adapter should be listed as VirtualBox Graphics Adapter and the Driver Provider should be Oracle Corp.

So it is.

---

### Post by .... on 2011-09-19
Then the "GPU is fully recognized and running."

---

