---
title: "Any Way to Get OpenGL 3.3 under 18.04 for Intel i915"
date: 2020-03-11
forum: Hardware
---

### Post by rebeltaz on 2020-03-11
Blender 2.8 will not run under anything less than OpenGL 3.3. This is my current hardware:

```
 
glxinfo | grep "OpenGL version"
OpenGL version string: 2.1 Mesa 20.1.0-devel (git-0103f02 2020-03-07 bionic-oibaf-ppa)

```

```

sudo lshw -C video
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
       resources: irq:26 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5050(size=8) memory:c0000-dffff

```

---

### Post by mörgæs on 2020-03-11
OpenGL 4.0 was born ten years ago. If this is a desktop computer you could see which kind of sockets / connectors are available and search for a used (say) eight years old graphics card.

---

### Post by rebeltaz on 2020-03-11
> **mörgæs said:**
> OpenGL 4.0 was born ten years ago. If this is a desktop computer you could see which kind of sockets / connectors are available and search for a used (say) eight years old graphics card.

Nah, it's a laptop. So guess I need to look for a newer one. Thanks.

---

### Post by Yellow Pasque on 2020-03-13
To answer the question more generally, no, you cannot magically get a newer OpenGL version than what your GPU hardware supports. "Core Processor Integrated Graphics Controller" sounds like an original Core Solo or Core Duo system, and those IGP's don't support OpenGL 3.x.
You could try forcing software acceleration (llvmpipe), but performance will be abysmal even if it works, especially with such an old system.
If no further questions, please mark the thread SOLVED (thread tools menu above first post)

---

### Post by rebeltaz on 2020-03-20
> **Yellow Pasque said:**
> To answer the question more generally, no, you cannot magically get a newer OpenGL version than what your GPU hardware supports. "Core Processor Integrated Graphics Controller" sounds like an original Core Solo or Core Duo system, and those IGP's don't support OpenGL 3.x.
You could try forcing software acceleration (llvmpipe), but performance will be abysmal even if it works, especially with such an old system.
If no further questions, please mark the thread SOLVED (thread tools menu above first post)

I always forget to do that. Thanks for reminding me. 

I might actually try llvmpipe, just for the hell of it. Thanks again.

---

