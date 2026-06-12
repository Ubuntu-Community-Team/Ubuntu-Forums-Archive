---
title: "fglrx with kernel 3.5.0-22 in 12.04LTS"
date: 2013-01-12
forum: Hardware
---

### Post by ballem on 2013-01-12
Running 12.04LTS on my Acer 5738G which has a mobility Radeon 4750, and have been trying to get fglrx to load with kernel 3.5.0-x. It works fine with kernel 3.2.0-x. Have tried both the manual patch as per the wiki and the makson PPA but whenever I boot into the 3.5 kernel fglrx fails to load with errors such as Major opcode of failed request: 139 (ATIFGLEXTENSION). Anyone know if there's a version of fglrx that works with the latest 3.5 kernel on 12.04?

```
inxi -SGx
System:    Host: laptop1 Kernel: 3.2.0-36-generic-pae i686 (32 bit, gcc: 4.6.3) Desktop: Gnome Distro: Ubuntu 12.04 precise
Graphics:  Card: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series] bus-ID: 01:00.0 
           X.Org: 1.11.3 driver: fglrx Resolution: 1366x768@60.1hz 
           GLX Renderer: ATI Mobility Radeon HD 4500/5100 Series GLX Version: 3.3.11653 - CPC Direct Rendering: Yes

fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500/5100 Series
OpenGL version string: 3.3.11653 Compatibility Profile Context
```

AMD driver lists itself in Catalyst control center as Driver packaging version: 8.97.100 but the install file is listed as amd-driver-installer-12.6-legacy-x86.x86_64.run

---

### Post by 2F4U on 2013-01-12
The AMD site for the driver version 12.6 states that it is supported for kernel up to 3.4:

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

From you post it seems as if you are running kernel 3.5, which, according to AMD, is not supported by this driver version.

---

### Post by ballem on 2013-01-12
> according to AMD, is not supported by this driver version

Yes I know that, there is a patch to work around that but I can't get it to work on my setup hence my post.

---

### Post by Yellow Pasque on 2013-01-12
Here's an old post I made when Catalyst 12-4 needed a patch. Maybe it will give you a guide on how to patch fglrx/Catalyst and make .debs out of it: [http://ubuntuforums.org/showthread.php?t=2104129](http://ubuntuforums.org/showthread.php?t=2104129)

---

### Post by ballem on 2013-01-13
> [http://ubuntuforums.org/showthread.php?t=2104129](http://ubuntuforums.org/showthread.php?t=2104129)
Thx for the reply but that link seems to point to a post about wifi drivers.

---

### Post by Yellow Pasque on 2013-01-13
Oh, sorry (copy/paste mishap). Here you go: [http://ubuntuforums.org/showthread.php?t=1969827](http://ubuntuforums.org/showthread.php?t=1969827)

---

