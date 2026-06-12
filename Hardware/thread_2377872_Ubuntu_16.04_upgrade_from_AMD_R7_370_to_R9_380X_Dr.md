---
title: "Ubuntu 16.04 upgrade from AMD R7 370 to R9 380X Driver Problems"
date: 2017-11-17
forum: Hardware
---

### Post by frwiley on 2017-11-17
I upgraded my graphics card to a card I found that would work with 16.04  and AMDGPU-PRO. I installed the card and the new drivers according to  AMD's instructions and the symptoms began by locking up the computer  when the login screen appeared. I can get everything to work with  "nomodeset" specified, but then of course I don't get any 3D  acceleration. I tried remove/install xorg-xserver and now I've lost any  configuration for X and X -configure now tells me "No devices to  configure." 

So the short version is that by trying to fix it, I have made it much  worse. I have a lot of time in configuring this environment and would  like to rescue it instead of reinstalling. I'm not new to Linux, but I  am quite stuck at this point. Any help appreciated.

The system is presently booting into low graphics mode. I have command  prompt access only, so it's hard to copy the log files into a browser.

Ubuntu 16.04.4
kernel 4.10.0.38
AMDGPU-Pro 17.40-492261

lspci:
```
01:00.0 VGA Compatible controller: Advanced Micro Devices, Inc.  [AMD/ATI] Tonga XT / Amethyst XT [Radeon R9 380x / R9 M295X] (rev  f1)
```

A few relevant lines from Xorg.0.log:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-38-generic root=UUID=... ro quite splash vt.handoff=7
xorg-server 2:1.18.4-0ubuntu0.7
list of loading modules including amdgpu_drv, ait_drv, nouveau_drv,  qxl_drv, radeon_drv, vmware_drv, fbdev_drv, vesa_drv, modesetting_drv,  intel_drv, and AMDGPU
falling back to old probe method for fbdev then vesa, then modesetting
[977.931] No devices to configure. Configuration failed.
```

Thanks?

---

### Post by frwiley on 2017-11-17
Went ahead and grabbed an old Windows 7 image on a hard drive to see if I could get the card to work in any other environment. Windows 7 is doing the same thing when I install the AMD drivers. Looks like this time was bad hardware. Now to figure out how to restore X when I put my old card back in.

---

### Post by wildmanne39 on 2017-11-17
There is also a bug in the driver for windows 7 concerning AMD drivers so that is probably what is causing the issue with windows 7 too and not defective hardware, you can google the windows issue and amd driver to find a fix, but this is not the forum for a windows discussion.

---

### Post by frwiley on 2017-11-18
In that case, are you interested/able in helping me getting it working in Ubuntu 16.04? Let's leave Windows out of it.

---

### Post by wildmanne39 on 2017-11-18
I have a different amd card but I think it will work with yours but I can not promise that. I had tried everything I could find for a year and nothing worked until this new kernel came out with amd improvements.

[https://github.com/M-Bab/linux-kernel-amdgpu-binaries](https://github.com/M-Bab/linux-kernel-amdgpu-binaries)

I get errors during boot but everything works so I do not worry about them.

---

### Post by frwiley on 2017-11-18
These kernel optimizations look like they enable/optimize for the amdgpu open-source drivers. Is this the same as the "gallium" drivers even on GCN 1.1+ cards? Because the installer for the application I bought this card for (x-plane 10) refuses to install if the gallium drivers are active. This is the reason I was willing to buy a new card to enable amdgpu-pro. X-Plane is a necessity for me.

---

### Post by frwiley on 2017-11-29
Ubuntu doesn’t seem to be built for this. Have given up and reinstalled Windows.

---

### Post by QIII on 2017-11-29
Unfortunate.  I'm running an R9 380X without problems, so saying Ubuntu is not made for this isn't quite true.  In fact, due to the longstanding relationship between AMD and Canonical, those two companies worked closely on the driver and it was initially released specifically targeted at Ubuntu.

---

