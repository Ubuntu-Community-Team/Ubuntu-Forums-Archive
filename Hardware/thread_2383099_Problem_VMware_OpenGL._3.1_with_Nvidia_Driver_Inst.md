---
title: "Problem VMware OpenGL. 3.1 with Nvidia Driver Installed"
date: 2018-01-20
forum: Hardware
---

### Post by psyclone on 2018-01-20
Hi,
I've got the following Nvidia Driver installed which runs the 3D Accelerated Graphics great. But I'm attempting to run  Autodesk ReCap and the program can't start due to missing OpenGL 3.1 (or greater). Where am I going wrong, I can provide the graphics-card model if that will help. 

```

e1desktop@e1desktop-MS-7788:~$ dpkg -l | grep -i nvidia*
ii  bbswitch-dkms                                               0.8-3ubuntu1                                 amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-340                                                340.106-0ubuntu0+gpu16.04.2                  amd64        NVIDIA CUDA runtime library
rc  nvidia-304                                                  304.137-0ubuntu0~gpu16.04.1                  amd64        NVIDIA legacy binary driver - version 304.137
ii  nvidia-340                                                  340.106-0ubuntu0+gpu16.04.2                  amd64        NVIDIA binary driver - version 340.106
rc  nvidia-opencl-icd-304                                       304.137-0ubuntu0~gpu16.04.1                  amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-340                                       340.106-0ubuntu0+gpu16.04.2                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.8.2                                        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             390.12-0ubuntu0~gpu16.04.1                   amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by psyclone on 2018-01-21
[IMG]/home/e1desktop/Desktop/Untitled 1.jpg[/IMG]

---

### Post by Yellow Pasque on 2018-01-21
^Your previous post didn't work correctly.

So you're running within a VM? Can you show output of:
```
glxinfo | grep string
```

>  can provide the graphics-card model if that will help. 
Wouldn't it have been faster to type the model of the GPU than to type that?

---

### Post by psyclone on 2018-01-21
Yes I'm running VM workstation player 14. The graphics card: Asus EN210.

```

e1desktop@e1desktop-MS-7788:~$ glxinfo | grep string
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL core profile version string: 3.3.0 NVIDIA 340.106
OpenGL core profile shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL version string: 3.3.0 NVIDIA 340.106
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL ES profile version string: OpenGL ES 2.0 NVIDIA 340.106 340.106
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.00

```

---

### Post by Yellow Pasque on 2018-01-22
Autodesk claims it will not work with VMWare: [https://knowledge.autodesk.com/support/recap/troubleshooting/caas/sfdcarticles/sfdcarticles/Recap-crashes-when-trying-to-run.html](https://knowledge.autodesk.com/support/recap/troubleshooting/caas/sfdcarticles/sfdcarticles/Recap-crashes-when-trying-to-run.html)
And it seems like other folks are having the issue
[https://forums.autodesk.com/t5/recap-forum/recap-360-in-a-vmware-virtual-machine/td-p/6606372](https://forums.autodesk.com/t5/recap-forum/recap-360-in-a-vmware-virtual-machine/td-p/6606372)

Your output shows the graphics driver is correctly installed and offers OpenGL 3.3 for both compatibility and core profile contexts.

---

### Post by psyclone on 2018-01-22
Thank-you Temüjin for your time, it is much appreciated.

---

