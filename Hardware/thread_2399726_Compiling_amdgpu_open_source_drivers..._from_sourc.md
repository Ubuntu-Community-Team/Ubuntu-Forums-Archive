---
title: "Compiling amdgpu open source drivers... from source"
date: 2018-08-29
forum: Hardware
---

### Post by mikishapiro on 2018-08-29
Hi

I'm running an experimental rig made up of an aarch64 (/ARM64 - same thing nowadays) system with PCIe and an AMD GPU sitting in its PCIe slot. 

The SoC is an armada 3720 SoC and the board is a Marvell Espressobin if that matters. 
# uname -a
Linux arm64box.localdomain 4.4.52-armada-17.10.4-g719fc86-dirty #7 SMP PREEMPT Tue Jul 3 10:59:53 UTC 2018 aarch64 aarch64 aarch64 GNU/Linux

The AMD GPU is recognised by lspci:
# lspci |grep AMD
00:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67df (rev e7)
00:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aaf0

For better or worse, I'm sitting on Xenial.
# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"

I need the kernel-space amdgpu driver. Not the whole stack (as described here: [https://github.com/GPUOpen-Drivers/AMDVLK](https://github.com/GPUOpen-Drivers/AMDVLK)).. just the kernel module compatible with my system.
AMD don't talk about the Vulkan driver in anything other than x86 context, but its source is available (and it is in the mainline x86 kernel). 

Context: this is to run a headless opencl GPU compute node, not a graphical X server, so I don't need the userspace stuff.

I have a full dev environment (and enough ram+swap) on the above boards so I should be tooled up sufficiently to build it locally.

I'm not very familiar with the debian/ubuntu multiverse, so am here asking - what's the best way to go about rebuilding amdgpu from source? (eg are there easily accessible source packages I can grab that already get used to build a binary amdgpu module deb packages or similar for our x86_64 xenial cousin?)

I also grabbed the latest kernel source - the drm/amdgpu driver is in the sources tree but "make menuconfig" isn't letting me pick it on the arm64 system...

What's the path of least resistance to compile this guy?

---

