---
title: "[ubuntu] Installing Driver for GTX 750 TI"
date: 2015-02-21
forum: Hardware
---

### Post by bizhat on 2015-02-21
My old graphics card AMD HD5670 died today. I got new GTX 750 TI. Now graphics is displayed with out proper driver (very low resolution).

I am using Ubuntu 14.04 64 bit.

glxinfo says.

```

boby@fwhlin:~ $ glxinfo | grep -i OpenGL
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL extensions:
boby@fwhlin:~ $

```

lshw -C Video

```

boby@fwhlin:~ $ sudo lshw -C Video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff
boby@fwhlin:~ $ 

```

I tried installing nvidia-current, but i get blank screen after that. So i uninstalled it.

Any suggestion to get it working ?

I just installed driver from ppa

```

sudo add-apt-repository ppa:xorg-edgers/ppa -y
sudo apt-get update
sudo apt-get install nvidia-346

```

Result

[https://gist.github.com/hostonnet/23f14c0f03efa1b700f8](https://gist.github.com/hostonnet/23f14c0f03efa1b700f8)

Going to reboot and see if it works. If no desktop, i will update this thread from mobile.

Look like it worked. Now graphics is normal. I will do some more test with games and see if all are ok.

```

boby@fwhlin:~ $ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 750 Ti/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 346.35
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 346.35
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
boby@fwhlin:~ $ 

```

---

