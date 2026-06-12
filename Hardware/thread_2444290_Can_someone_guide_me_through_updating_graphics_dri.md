---
title: "Can someone guide me through updating graphics drivers?"
date: 2020-05-28
forum: Hardware
---

### Post by gamerwael on 2020-05-28
I'm having trouble running blender 2.8. Whenever I start it I get:
```

Error! Unsupported graphics card or driver.
A graphics card and driver with support for OpenGL 3.3 or higher is required.
The program will now close.

```

The output of ```
sudo lshw -c video
```is
```
  *-display                 
       description: VGA compatible controller
       product: Park [Mobility Radeon HD 5430/5450/5470]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4050(size=8) memory:c0000-dffff

```

The output of ```
lspci -nnk | grep -i vga -A3 | grep 'in use'
```is
```
Kernel driver in use: i915
    Kernel driver in use: radeon

```

The output of```
lspci -k | grep -EA3 'VGA|Display|3D'
``` is
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Hewlett-Packard Company Core Processor Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
    Subsystem: Hewlett-Packard Company Park [Mobility Radeon HD 5430/5450/5470]
    Kernel driver in use: radeon
    Kernel modules: radeon

```

The output of ```
glxinfo | grep OpenGL
```is
```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 19.2.8
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 19.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:

```

---

### Post by Yellow Pasque on 2020-05-28
Driver upgrade is not the answer. It will not magically take your old Intel GPU from OpenGL 2.x to OpenGL 3.3 
The (possible) solution is to run on the AMD GPU, which should support OpenGL 3.3:
```
DRI_PRIME=1 blender
```

---

### Post by gamerwael on 2020-05-28
Blender opens for a split second and then crashes. I get the following in the terminal:
```
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: The kernel rejected CS, see dmesg for more information (-16).
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 0
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 4096 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
EE ../src/gallium/drivers/r600/r600_texture.c:1442 r600_texture_transfer_map - failed to create temporary texture to hold untiled copy
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
radeon: Failed to allocate a buffer:
radeon:    size      : 1048576 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 2
radeon:    flags     : 4
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  149 ()
  Minor opcode of failed request:  2
  Serial number of failed request:  201
  Current serial number in output stream:  206
Writing: /tmp/blender.crash.txt
Segmentation fault (core dumped)

```

---

### Post by Yellow Pasque on 2020-05-28
It looks like you don't have enough video RAM. Make sure your system meets requirements: [https://www.blender.org/download/requirements/](https://www.blender.org/download/requirements/)

---

### Post by gamerwael on 2020-05-28
It looks like I'm missing a few requirements... Isn't there any other way?

---

### Post by Yellow Pasque on 2020-05-28
Try older versions of Blender as the page suggests?

---

### Post by gamerwael on 2020-05-28
Older versions work properly. I guess I'll stick with that. Another problem that I was facing was with Unity Game Engine. Whenever I try to launch the editor I get a fatal error: Failed to initialize Unity graphics.
Any ideas on how to fix this? Thanks for the help so far.

---

### Post by Yellow Pasque on 2020-05-28
> **gamerwael said:**
>  Another problem that I was facing was with Unity Game Engine. Whenever I try to launch the editor I get a fatal error: Failed to initialize Unity graphics.

Again, try running the command with DRI_PRIME=1 to use the AMD GPU. The Intel GPU does not meet Unity's OpenGL 3.x requirement.
If that doesn't work, it may be time to consider a better/newer laptop if you want to do intensive 3D tasks.

---

### Post by gamerwael on 2020-05-28
Thanks for the help, but it didn't work. My laptop is pretty old.

---

### Post by QIII on 2020-05-28
You have two problems --

1. Your AMD card is not supported.

2.  Yours is a hybrid AMD/Intel graphics system, for which the OEMs do not provide a good solution for Linux.


You may disregard any suggestion of AMDGPU.  Your card is old not supported by it.  AMDGPU works only with hardware that is GCN 1.1 (Graphics Core Next) or later, although there is experimental support for GCN 1.0.  Your card is several technologies older than GCN.

Assuming you had a purely AMD system:  There are two drivers for AMD graphics cards now:  the amdgpu and radeon kernel modules.  (AMDGPU-PRO is a proprietary overlay to amdgpu and it does not support all cards).  When you install Ubuntu (among other Linux distros) the installer decides if your graphics card is supported by radeon or amdgpu and loads the appropriate module.  Your system will have radeon loaded.

You can check this by issuing the following command in the terminal:

```
lsmod | grep radeon
```

This may return several lines, depending on your hybrid system.

```
lsmod | grep amdgpu
```

should return nothing.

You *might* be able to target your Intel graphics by disabling the AMD GPU in your BIOS, but even your Intel GPU may not be up to the task.

---

