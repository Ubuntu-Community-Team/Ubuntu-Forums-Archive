---
title: "Vulkan stopped working?"
date: 2020-09-11
forum: Hardware
---

### Post by canhoto on 2020-09-11
Hi. 
  After a few days using X-Plane 11.50r3 with Vulkan running I began having this message and I  can't activate Vulkan: 
> Vulkan driver is not supported on this computer. An extension required to run the OpenGl bridge is not supported on llvmpipe (LLVM 10.0.0, 128 bits)

  I am using the Nvidia proprietary driver (440), so... 
  I'm using Ubuntustudio 20.04, my graphics card is a Nvidia 1050 Ti and the processor a Ryzen 5 3600X. 
  And, as I said, until yesterday all was working fine. 
 
Any idea of what may be causing this?

---

### Post by CelticWarrior on 2020-09-11
"llvmpipe" suggests the Nvidia drivers aren't being loaded.
If they're really installed then try disabling Secure Boot in UEFI. It may have been turned on again with a UEFI update.

---

### Post by canhoto on 2020-09-11
Thanks. I'll check this.

---

### Post by canhoto on 2020-09-11
I checked that, but Secure Boot is disabled.

---

### Post by CelticWarrior on 2020-09-11
Open Additional Drivers and confirm the drivers are installed, re-select and reapply if necessary.

---

### Post by canhoto on 2020-09-11
> **CelticWarrior said:**
> Open Additional Drivers and confirm the drivers are installed, re-select and reapply if necessary.

It seems it's being used. And if I type ```
lspci -v
```, I have this, regarding the controller:
> 2b:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. GP107 [GeForce GTX 1050 Ti]
    Flags: bus master, fast devsel, latency 0, IRQ 70
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia


The only thing that I changed since yesterday is the Java version. I was running the default jre (Openjdk 11) and I replaced it with an Oracle one (8u241). But this should have nothing to do with the graphics, I guess.

---

### Post by canhoto on 2020-09-11
But if I type ```
glxinfo -B
```, I'll have the following output:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 10.0.0, 128 bits) (0xffffffff)
    Version: 20.0.8
    Accelerated: no
    Video memory: 16022MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 10.0.0, 128 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.1 Mesa 20.0.8
OpenGL shading language version string: 1.40
OpenGL context flags: (none)

OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10


```

---

### Post by canhoto on 2020-09-11
Well, you were right. The nvidia driver wasn't completely installed. I solved it by installing the metapackage from the terminal:
```
sudo apt install nvidia-driver-440
```

After rebooting, the problem with Vulkan was solved, and I now have the following output from ```
glxinfo | grep OpenGl
```:

```
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 1050 Ti/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 440.100
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 440.100
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 440.100
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:


```

Thanks! You guided me into the right path!

---

