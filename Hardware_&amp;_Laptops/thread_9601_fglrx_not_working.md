---
title: "fglrx not working"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by mattblack_uk on 2004-12-29
I could do with some help here please...
I have followed the binary driver howto for ati drivers by doing the following:

installing linux-k7, linux restricted modules, linux headers
Installing fglrx-driver, fglrx-driver-dev, fglrx-control
(These are version 2.6.8 I think, from the warty repository.)
echo fglrx | sudo tee -a /etc/modules
Edit XF86Config-4 and change "ati" to "fglrx" in the device section
Remove the nvidia module, nvidia.ko, from the appropriate directory.

This has worked as far as enabling 3d, but the default screen resolution is not what I require. I would like it to default to 1024*768. When I try the screen rsolution option under the system configuration menu, it gives me an error, "The X Server does not support the XRandR extension"

Searching through other posts, it seems that the best way to get around this is to run fglrxconfig and choose default screen resolutions. The problem is when I do this, I can no longer boot into X. I have tried various options eg, use external agpgart = y and =n. For most of the other options I leave them set on default, or choose the safe option. My horizontal and Vertical ranges are definately correct. Anybody got any ideas?

Just one more thing... Is there any way of changing the monitors refresh rate without going into system configuration >> screen resolution? I like to have mine set on 70hz

---

### Post by pmshoop on 2005-01-06
[QUOTE=mattblack_uk]I could do with some help here please...
I have followed the binary driver howto for ati drivers by doing the following:

Where did you find this how-to?  I'm trying to get 3D support working for my ATI driver now and can't for the life of me figure out which modules to install... there are quite a few.  any help would be appreciated.

Paul.

EDIT:  I got all that installed... just need to know how to edit XF86Config-4 file... I cant find it anywhere... where is the file hidden?

---

### Post by fng on 2005-01-06
You can find it here : /etc/X11/XF86Config-4

---

