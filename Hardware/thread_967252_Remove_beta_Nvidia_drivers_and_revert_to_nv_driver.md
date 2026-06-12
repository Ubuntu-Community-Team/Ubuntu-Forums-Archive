---
title: "Remove beta Nvidia drivers and revert to nv driver (8.10)"
date: 2008-11-01
forum: Hardware
---

### Post by TiberiusDRAIG on 2008-11-01
Hi, I installed the beta drivers for legacy Nvidia cards in Intrepid only to find that all it has done is made the system unstable and my screen blurry. Compiz still doesn't work correctly either, with all of my window decorations missing and terminals displaying as blank white boxes. 

I was wondering if there was any way I could purge the beta drivers and restore the original nv driver? I'm happy to wait until there's an official release now that I know the beta is useless, but I just had to check =P

Cheers

Update: 
[QUOTE NAME="vmatherly"]You just need to edit your /etc/X11/xorg.conf file

change

Code:

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 4"
EndSection

to

Code:

Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 4"
EndSection

or at the command line run

Code:

$ sudo dpkg-reconfigure xserver-xorg

[/QUOTE]

---

### Post by ardvark71 on 2008-11-01
Hi...

There should be a stable package for legacy Nvidia cards in Synaptic that might give you more capability than the "nv" driver. I've used it before and it seemed to do pretty well. :)

Best Regards...

---

### Post by TiberiusDRAIG on 2008-11-01
From the Intrepid Release Notes:
> nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 

Unfortunately, I'm using a Geforce 4400ti so no driver support for me just yet =/

---

### Post by ardvark71 on 2008-11-02
> **TiberiusDRAIG said:**
> 
Unfortunately, I'm using a Geforce 4400ti so no driver support for me just yet =/

Hi...

I'm very sorry and disappointed to learn of this. :( I'm sure there are quite a few folks out there who have cards listed in the summary you included. 

You might have already been here but I would think Nvidia would have a functional stable driver for your card, with 3D acceleration...

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Best Regards...

---

