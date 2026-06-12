---
title: "nVidia Direct Rendering and 3D resets"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by rykel on 2005-06-05
Hi,

I removed nvidia-glx and went for a clean install of the official nvidia driver from nvidia.com.

I have a FX 5700 card.

It works great!

GlxGears gives me more than 1500 fps consistently, and my DivX anime and DVDs all work flawlessly without choppiness in Totem. My favourite autopackage-installed SuperTux and Lincity-ng would run perfectly.

HOWEVER, after every reboot, I would "lose" the 3D and glxgears would give me a segmentation fault. None of the 3D games would even start.

In order to reolve the problem, I would have to reinstall the official driver, and in an instant, everything would be back to normal.

I have also commented out "dri" in /etc/X11/xorg.conf, instead of relying on the original "nvidia-glx-config enable" settings.

May I know if anybody can advise me on what else I might need to do in order to make my nvidia 3D capability permanent?

Also, I believe I can add something to the effect of "Enable 3D Acceleration" in /etc/X11/xorg/conf. Do you know what the line is, exactly?

btw, I get Direct Rendering ONLY with the official driver, never with nvidia-glx.

That was one reason why I removed the nvidia-glx package.

I will gladly revert to nvidia-glx since it is the default distro-given driver... IF I can get Direct Rendering.

Thanks for your help!!



Best Regards,


Rykel
Singapore

---

### Post by flanker on 2005-06-05
Have you added `nvidia` to /etc/modules ?
       i.e sudo echo nvidia >> /etc/modules

This will ensure the driver module is loaded on startup.

Adding the below line to the device section of /etc/X11/xorg.conf should help speed things up;
        Option          "RenderAccel"   "true"

ps. make sure when using either method you changed the driver in /etc/X11/xorg.conf from "nv" to "nvidia".

---

### Post by oritpro on 2005-06-05
I had a similar problem and it was because my previous driver came from the an official deb package through Synaptic.  The new Nvidia driver attempts to uninstall it but fails miserable with no indication.

The fix was to uninstall the deb driver package and re-install the new Nvidia driver package from nvidia.com.

Runs excellent now.  \\:D/

---

