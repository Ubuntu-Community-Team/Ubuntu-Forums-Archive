---
title: "AMD/AMD Dual Graphics"
date: 2016-12-18
forum: Hardware
---

### Post by gvalle-augusto on 2016-12-18
Hello everyone,

My first post here. So, straight to the point, I bought a MSI GX70 in 2014. It has an AMD A10 5750m with the integrated HD 8650g GPU (aruba) and also an HD 8970m as the dedicated one (pitcairn)

The dedicated GPU does not work. Does not matter what I do, and

**```
xrandr --setprovideroutputsink 0 1
```** also does not work. The following error comes out:
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
```

DRI_PRIME is not able to use the dedicated GPU.: eg: when using **```
glxinfo | grep OpenGL
``` **and **```
DRI_PRIME=1[B] glxinfo | grep OpenGL**
```[/B]the output is the same: Aruba (Hd 8650g)
I installed steam and the performance is the same in any game, with or without DRI_PRIME=1

I also tried to use vgaswitcheroo and **```
sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
``` **actually shows the dedicated GPU, but as "dynOFF". Then I tried to boot up with ```
radeon.runpm=0
```, and the dedicated GPU finally showed up as "Pwr", but it still didn't work (no performance gain with or without DRI_PRIME). The performace was the same as it was using only the integrated one.

I'm currently using Ubuntu 16.10 and ```
**$ xrandr --listproviders**
``` is perfectly able to outpout both the GPUs, which means that they are being recognized.

Could anyone help me?

---

### Post by gvalle-augusto on 2016-12-19
Going up

---

### Post by slickymaster on 2016-12-19
*Thread moved to **Hardware**.*

---

### Post by gvalle-augusto on 2016-12-22
up

---

### Post by gvalle-augusto on 2017-01-04
so, can anyone help?

---

### Post by QIII on 2017-01-04
You may be in a world of hurt right now with the changes in the landscape of AMD drivers.

As you may or may not know, fglrx is gone.

When you install 16.04 and beyond, the installer determines which open source driver to install:  Radeon or AMDGPU.  It may not be adding both GPUs or the HD 5000 series takes the Radeon driver and the HD 8000 series will take the AMDGPU driver in 16.10.  In the first case, you will only get one of the GPUs and in the second you will probably get some sort of clash.

Unfortunately, I don't have a Dual GPU laptop to experiment on.

fglrx had been updated to the point that one could run two GPUs (you could not change on the fly, though) without vgaswitcheroo.  But I think you would have to use 14.04 or 14.04.1 to avoid graphics stack and HWE issues.

---

### Post by gvalle-augusto on 2017-01-06
> **QIII said:**
> You may be in a world of hurt right now with the changes in the landscape of AMD drivers.

As you may or may not know, fglrx is gone.

When you install 16.04 and beyond, the installer determines which open source driver to install:  Radeon or AMDGPU.  It may not be adding both GPUs or the HD 5000 series takes the Radeon driver and the HD 8000 series will take the AMDGPU driver in 16.10.  In the first case, you will only get one of the GPUs and in the second you will probably get some sort of clash.

Unfortunately, I don't have a Dual GPU laptop to experiment on.

fglrx had been updated to the point that one could run two GPUs (you could not change on the fly, though) without vgaswitcheroo.  But I think you would have to use 14.04 or 14.04.1 to avoid graphics stack and HWE issues.

So, is there any hope of making it work?
I've seen people with similar setups messing with /etc/X11/xorg.conf or something like that, so ubuntu used the correct drivers for the correct GPU. Though I don't think this is the problem, since both GPUs are recognized without any problem, the only thing is that I cannot switch to the dedicated one, does not matter what I do.

Another thing I found and it may be interesting: When using DRI_PRIME=1 with glxgears, my FPS count is way higher (like, 2000 FPS if I can remember correctly), while without PRIME I can get 60 FPS (monitor refresh rate). To sum it up: Prime for me is not working as a GPU switch tool, but only sort of cancelling V-Sync. 

Also, the system boots up normally with 3D acceleration due to the integrated GPU. But after running dmesg I found something regarding the dedicated one:
```
 "radeon: ring 0 test failed" followed by  "radeon: disabling GPU acceleration''
```
One more thing: I remember using vgaswitcheroo to change graphics card after killing X
```
sudo echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```

And the screen went black after hanging for a few moments, but the system was still running as I managed to shut it down via command line without seeing what was happening on the screen (lol)
I just wanted to move away from all the problems and bugs windows 10 is giving me with this computer, but at the moment I have nowhere to run.

---

### Post by gvalle-augusto on 2017-01-12
Up

---

