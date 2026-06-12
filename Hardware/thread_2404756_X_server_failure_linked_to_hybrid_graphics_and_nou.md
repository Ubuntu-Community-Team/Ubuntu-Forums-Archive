---
title: "X server failure linked to hybrid graphics and nouveau prime [18.04]"
date: 2018-10-28
forum: Hardware
---

### Post by folquet on 2018-10-28
Dear Ubunteers, 

first time poster here; apologies in advance if I get anything wrong in terms of forum protocols. I have considered posting [here]("https://ubuntuforums.org/showthread.php?t=1743535") but seeing how that thread is over 100 pages long, I figured it was better to start a new one, and possibly incorporate any findings there, if/when the problem is solved. 

I have encountered a major issue with my Ubuntu unit, which I have been trying to solve for the past month or so. I am reasonably literate when it comes to computers, but my knowledge of the command line is limited, so I have had put together bits and pieces as I go along, to troubleshoot in a sensible way and also (hopefully) learn something in the process. 

To the best of my understanding, the issue is connected to the well-attested can-of-worms that are the **nvidia proprietary drivers**. 

Here is the backstory: I have used trusty for years, and all was well. I have a hybrid graphics card, and I believe I was using the 'nvidia prime' functionality of the **open-source nouveau driver**, to switch off and on the NVIDIA GPU. Then, at some point, some update must have broken the settings, and when I tried to switch on the NVIDIA card again things would stop working. I kept using the Intel setting, and looked for a fix. 

First I updated to xenial, and started noticing long delays during boot. In an effort to fix those, I updated the official nvidia drivers, and that 'broke' the kernel altogether, throwing me into a hell pit of black-screens-on-boot. I finally tried updating to 18.04 - no joy. End of backstory. 

And here is what I have done so far. I removed and re-installed the nvidia drivers, then:

in **etc/modprobe.d/nvidia-graphics-driver.conf **I have added:

 ```
blacklist nouveau
blacklist lbm-nouveau

```

I have also  added: 

```
nvidia-drm-modeset=1
``` 

to **GRUB_CMDLINE**. 

 And I have disabled **'nvidia-fallback-service'** using ```
systemctl disable nvidia-fallback.service
```

None of this helped, and - admittedly - I have at best a tenuous grasp of what it was meant to achieve anyway. Removing the nvidia drivers altogether did result in the system booting successfully, but then the GUI was laggy and borderline unusable.

Eventually, because this is my primary machine and I need it to work on a day-to-day basis, I had to devise a fallback solution, so I reinstalled the nvidia drivers, and modified the grub settings to use an old kernel as a default. My system is now running kernel version 3.13. It boots normally, and the Intel setting appears to be functioning, even though prime-select query returns 'nvidia' (attempt to set prime-select to 'intel' fails due to 'packages not supporting prime'). 

I am conscious that this is only a temporary backstop, and am keen to find a more permanent solution. I should also note that I do not massively care about the nvidia GPU actually working, at this point. All I need is for the prime Intel setting to work smoothly with a current kernel. 

I appreciate that a magical fix does not exist, but would anyone here be able to help me understanding the problem, or direct me in any useful direction? Should I just give up and try a fresh install?

Thanks in advance for any advice or suggestions.

(meanwhile, here are the printouts of some exploratory commands I picked up in my forum-scouting, in case they are useful)

```
mu@Pr0teus:~$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
 Vendor: Intel Open Source Technology Center (0x8086)
 Device: Mesa DRI Intel(R) Haswell Mobile  (0x416)
 Version: 18.0.5
 Accelerated: yes
 Video memory: 1534MB
 Unified memory: yes
 Preferred profile: core (0x1)
 Max core profile version: 3.3
 Max compat profile version: 3.0
 Max GLES1 profile version: 1.1
 Max GLES[23] profile version: 3.1
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.0.5
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.0 Mesa 18.0.5
OpenGL shading language version string: 1.30
OpenGL context flags: (none)

OpenGL ES profile version string: OpenGL ES 3.0 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
```

```
mu@Pr0teus:~$ lspci | egrep 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)
```

```
mu@Pr0teus:~$ dpkg -l | egrep 'nvidia'
ii  libnvidia-cfg1-390:amd64    390.48-0ubuntu3amd64   NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390   390.48-0ubuntu3allShared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64 390.48-0ubuntu3amd64   NVIDIA libcompute package
ii  libnvidia-compute-390:i386  390.48-0ubuntu3i386    NVIDIA libcompute package
ii  libnvidia-decode-390:amd64  390.48-0ubuntu3amd64   NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386   390.48-0ubuntu3i386    NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64  390.48-0ubuntu3amd64   NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386   390.48-0ubuntu3i386    NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64    390.48-0ubuntu3amd64   NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386390.48-0ubuntu3i386    NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64 390.48-0ubuntu3amd64   NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386  390.48-0ubuntu3i386    NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64    390.48-0ubuntu3amd64   NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386390.48-0ubuntu3i386    NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390    390.48-0ubuntu3amd64   NVIDIA compute utilities
ii  nvidia-dkms-390   390.48-0ubuntu3amd64   NVIDIA DKMS package
ii  nvidia-driver-390 390.48-0ubuntu3amd64   NVIDIA driver metapackage
ii  nvidia-kernel-common-390    390.48-0ubuntu3amd64   Shared files used with the kernel module
ii  nvidia-kernel-source-390    390.48-0ubuntu3amd64   NVIDIA kernel source package
ii  nvidia-prime 0.8.8allTools to enable NVIDIA's Prime
ii  nvidia-settings   390.42-0ubuntu1amd64   Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390  390.48-0ubuntu3amd64   NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390    390.48-0ubuntu3amd64   NVIDIA binary Xorg driver

```

```
mu@Pr0teus:~$ grep nvidia /etc/modules /etc/modprobe.d/*
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb

```

---

### Post by folquet on 2018-11-02
Updates: my backstop trick has now stopped working. I have blocked the rest of the day to work on the issue. I thought I'd bump my previous post, in case anyone out there has any suggestion.

---

### Post by folquet on 2018-11-03
Further updates.

I purged the proprietary nvidia drivers: that resulted in a new behaviour. I had the nouveau driver spamming error messages during the boot, then the GUI would load, and almost immediately freeze at the login page. 

I went back to etc/default/grub and added **nouveau.modeset=0** to CMDLINE DEFAULT, which fixed the freezing issue (see also [here]("https://askubuntu.com/questions/1053150/nouveau-modeset0")). I thought I was out of the woods, but alas, I am now experiencing a different graphical issue: the in-built monitor randomly flickers and eventually turns itself off. If I connecting a secondary monitor through a PCI cable, the second monitor works fine. 

In short, I am still in graphic card hell. 

If anyone is reading, any help would be appreciated. Would it make sense to try a fresh re-install?

Thank you.

---

