---
title: "NVIDIA 71.86.11 on Ubuntu 9.10"
date: 2009-11-26
forum: Hardware
---

### Post by mouratos1a on 2009-11-26
Dear all,
I have a Desktop PC loaded with Legend QDI Platinix-2 
NViDIA Riva TNT2 64
P-4 Socket 478 2 GHz

I am trying to install nvidia drivers in order to improve speed especially on moving objects...
I downloaded the driver from Nvidia : NVIDIA-Linux-x86-71.86.11-pkg1.run
I followed various recipes (especially [http://ubuntu.ubuntuforums.org/showthread.php?t=1125400](http://ubuntu.ubuntuforums.org/showthread.php?t=1125400) ) and tried various tricks with no obvious result...
I do install the driver but i cannot make it work...
It is not visible anywhere...
I tried System>Admin>Hardware Drivers with no success..
How can I check if it is active or not?
How can I activate it?
Many guys talk about Xorg...which does not exist on Karmic Koala...
Please advice...
Thank you all,
Mouratos of Greece

---

### Post by klemes on 2009-11-26
Hi mouratos,
from what I gather legacy NVIDIA drivers off the 71.86.xx series are incompatible with the current Xorg that Ubuntu 9.10 uses,and so is the nvidia-glx-71 driver that there was initially in the Ubuntu repositories but now is unavailable also.So no luck on this one I am afraid you have to stick with the open source `nv`driver.Your only other option is `nouveau` but for the TNT2 it lacks also 3D support although there is some good 2D hardware acceleration from what I have tested.Try them out if you will.

---

### Post by mouratos1a on 2009-11-26
Thanks alot...
Just gimme a small push with nouveau...What is this?
Thanks again

> **klemes said:**
> Hi mouratos,
from what I gather legacy NVIDIA drivers off the 71.86.xx series are incompatible with the current Xorg that Ubuntu 9.10 uses,and so is the nvidia-glx-71 driver that there was initially in the Ubuntu repositories but now is unavailable also.So no luck on this one I am afraid you have to stick with the open source `nv`driver.Your only other option is `nouveau` but for the TNT2 it lacks also 3D support although there is some good 2D hardware acceleration from what I have tested.Try them out if you will.

---

### Post by klemes on 2009-11-26
Nouveau is an independent open source alternative driver for Nvidia video cards that promises superior performance than the existing  nv and nvidia drivers for the Linux desktop.They are still at various alpha/beta/testing modes but that does not stop a lot of people from using them all the same. 
In Ubuntu you install them just issuing one command in the console:

```
sudo apt-get install xserver-xorg-video-nouveau
```After the downloading is over it will install nouveau driver nouveau_drm module and nouveau_kernel module which is build dynamically by DKMS.
After that simlpy add the line `* Driver    "nouveau"*   ' in the appropriate place in your _*xorg.conf*_ reboot and you are done.
You might also have a look at the Nouveau wiki page:
[http://nouveau.freedesktop.org/](http://nouveau.freedesktop.org/)

---

### Post by DandyAndy on 2009-11-26
Thank you, I (too) will try this. As it is now i have to start the computer with the live CD, mount the drive and delete xorg.conf everytime i reboot. I could probably delete xorg.conf before every boot now that i know whats going on...
Running without the driver makes my eyes hurt every time I scroll so it's not an option. I would like the 3d bits but thats just a dream by now.

---

