---
title: "Can't install Ubuntu 20.04 nvidia drivers - &quot;404 not found&quot;"
date: 2021-07-30
forum: Hardware
---

### Post by dewdrop_world on 2021-07-30
Looking to improve 3D graphics support. Ubuntu Studio 20.04. 

So:

```
$ sudo hwinfo --gfxcard --short
graphics card:                                                  
                       nVidia GM108M [GeForce 920MX]
                       Intel Skylake GT2 [HD Graphics 520]


Primary display adapter: #23
```

"HD Graphics 520" isn't the newest, but AFAICS it's newer than the minimum requirement for e.g. Touch Designer.

```
$ ubuntu-drivers devices
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
== /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 ==
modalias : pci:v000010DEd0000134Fsv000017AAsd0000505Cbc03sc02i00
vendor   : NVIDIA Corporation
model    : GM108M [GeForce 920MX]
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-470 - distro non-free recommended
driver   : nvidia-driver-460-server - distro non-free
driver   : nvidia-driver-460 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

"Recommended" sounds nice...

```
$ sudo apt install nvidia-driver-470
... snip
The following additional packages will be installed:
  libnvidia-cfg1-470 libnvidia-common-470 libnvidia-compute-470
  libnvidia-compute-470:i386 libnvidia-decode-470 libnvidia-decode-470:i386
  libnvidia-encode-470 libnvidia-encode-470:i386 libnvidia-extra-470
  libnvidia-fbc1-470 libnvidia-fbc1-470:i386 libnvidia-gl-470
  libnvidia-gl-470:i386 libnvidia-ifr1-470 libnvidia-ifr1-470:i386
  nvidia-compute-utils-470 nvidia-dkms-470 nvidia-kernel-common-470
  nvidia-kernel-source-470 nvidia-prime nvidia-settings nvidia-utils-470
  screen-resolution-extra xserver-xorg-video-nvidia-470
... snip
0 upgraded, 25 newly installed, 0 to remove and 1 not upgraded.
Need to get 269 MB/270 MB of archives.
After this operation, 787 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Ign:1 http://hk.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 libnvidia-cfg1-470 amd64 470.57.02-0ubuntu0.20.04.1
Ign:2 http://hk.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 libnvidia-common-470 all 470.57.02-0ubuntu0.20.04.1
... snip
Err:3 http://security.ubuntu.com/ubuntu focal-updates/multiverse i386 libnvidia-compute-470 i386 470.57.02-0ubuntu0.20.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:4 http://security.ubuntu.com/ubuntu focal-updates/multiverse amd64 libnvidia-compute-470 amd64 470.57.02-0ubuntu0.20.04.1
  404  Not Found [IP: 91.189.88.152 80]
... snip, over a hundred of these
```

Same result if I use the graphical Software & Updates app.

I had assumed that a recommended driver would be physically available on the servers, so I guess something has changed on the servers but perhaps not changed in the "ubuntu-drivers" utility...?

Searched google and here. I can't find any posts about this. New problem? Unique problem?

hjh

---

### Post by deadflowr on 2021-07-30
It's weird it's looking in the multiverse repository as the nvidia packages are all in the restricted repository.

---

### Post by dewdrop_world on 2021-07-31
> **deadflowr said:**
> It's weird it's looking in the multiverse repository as the nvidia packages are all in the restricted repository.

Hm, OK, how to resolve it then? 'restricted' is already enabled as a software source in my system.

hjh

---

### Post by TheFu on 2021-07-31
```
sudo ubuntu-drivers autoinstall
```
is all that should be needed for supported GPUs.  I don't know how old the GPU is. I do know that my 7200GS is NOT supported, but my 430GT and 1030GT are.

I have no idea how to get Linux to choose between nvidia and Intel igpu. Sorry.  My systems only have 1 GPU.  The intel igpu stuff "just works."

Google found the nvidia driver support page, which says 

> 
Linux x64 (AMD64/EM64T) Display Driver
 
Version: 	470.57.02
Release Date: 	2021.7.19
Operating System: 	Linux 64-bit
Language: 	English (US) 
So, that's the version that the autoinstall (top of my post) should install for you, if nvidia is the current GPU used.  Never manually download and install GPU drivers under ubuntu. Use the command at the top.

If the server with the code isn't available, you could try a different country repo or just wait a few hours or days until it comes back up.

---

