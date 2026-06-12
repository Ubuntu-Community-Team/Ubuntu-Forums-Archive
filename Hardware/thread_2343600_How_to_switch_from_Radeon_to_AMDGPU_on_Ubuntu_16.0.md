---
title: "How to switch from Radeon to AMDGPU on Ubuntu 16.04?"
date: 2016-11-17
forum: Hardware
---

### Post by myromance123 on 2016-11-17
Hey there, I'm on Ubuntu 16.04 64bit. I've manually compiled the latest kernel at this time, Kernel 4.9-RC5 and have it up and running no problem.

I made sure to tick CONFIG_DRM_AMDGPU_CIK before compiling it.

I have installed the Padoka PPA, so the following:
```
glxinfo | grep OpenGL
```
returns
```
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD BONAIRE (DRM 2.48.0 / 4.9.0-rc5, LLVM 4.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 13.1.0-devel - padoka PPA
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 13.1.0-devel - padoka PPA
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 13.1.0-devel - padoka PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

```

Even after restarting, I cannot seem to get the AMDGPU driver to run.
```
lspci -k | grep -EA2 'VGA|3D'
```
returns
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X/360]
	Subsystem: PC Partner Limited / Sapphire Technology Bonaire XTX [Radeon R7 260X/360]
	Kernel driver in use: radeon
```

This chip is a 2nd Gen GCN chip, so it should be a GCN 1.1 Sea Island chip. Hence why I ticked the CIK config above before compiling the kernel.

Before compiling my own kernel and installing it, when running:
```
lsmod | grep radeon
```

I would get:
```
radeon               1515520  4
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        159744  1 radeon
drm                   364544  65 radeon,ttm,drm_kms_helper
```

After installing the new kernel I get:
```
radeon               1499136  78
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   102400  2 amdgpu,radeon
drm_kms_helper        159744  2 amdgpu,radeon
drm                   364544  8 amdgpu,radeon,ttm,drm_kms_helper
```

So I clearly have the needed amdgpu parts. One thing I did not do is update the firmware for my card, as I don't know how to do this. I did read that some had to do this, but I'm uncertain if it's necessary in my case.

I have tried blacklisting radeon by use of the blacklist.conf file and also by trying to create a radeon.conf file in /etc/modprobe.d/ but no luck. No matter where I place the file, radeon is always defaulted to upon startup. I also have a 10-amdgpu-pro.conf in usr/share/X11/xorg.conf.d/ but it doesn't seem to change the scenario.

My question is how do I disable Radeon and force AMDGPU into play? I'm ok with breaking my system.

Why do I want to do this? I want to utilize the RADV Vulkan implementation, and this is the only way. Yes, I can use AMDGPU-PRO for Vulkan, and I already have. I specifically want to use RADV in this use case.

Any help is greatly appreciated!

---

### Post by richardsdma on 2016-11-18
I would like to know myself a method to make the switch, starting from scratch. it will be very useful.
my amd e2-7110 eats 30-40% more power than windows 10 while using radeon driver.

---

