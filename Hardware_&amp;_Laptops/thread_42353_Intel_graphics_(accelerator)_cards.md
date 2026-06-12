---
title: "Intel graphics (accelerator) cards?"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-06-17
I saw Intel has drivers for it's cards that are used in notebooks.
Are they any good, do they have 3D acceleration?

---

### Post by nocturn on 2005-06-17
They seem 2D only, although there are companies that sell 3D accelerated Linux drivers...

---

### Post by az on 2005-06-17
Onboard intel video chips are apparently the most common graphics chips on the market.

3d accelleration in free software is handled by DRI:

[http://dri.freedesktop.org/wiki/Intel?action=highlight&value=CategoryHardware](http://dri.freedesktop.org/wiki/Intel?action=highlight&value=CategoryHardware)

/QUOTE
Intel
Chipsets 


Status
Supported chipsets: 

i810 

i810-dc100 

i810e 

i810e2 

i815 

i815e 

i830 

i845 

i852/855 

i865 

i915 

Unsupported chips: 

i740. Intel claimed to have a Software Developer's Manual (order number 290617) available for this chip, but it is not posted on the website anywhere. The datasheet is available here, but this is a feature list only and is not useful for programming a DRI driver. The i740 appears to be the i810 minus multitexturing and anisotropic mipmap filtering, with slightly different register locations. 

i752. Brief-lived successor to the i740, and may in fact be identical to the i810. 
/QUOTE



Can anyone share their results? (glx gears scores)

---

### Post by jerome bettis on 2005-06-17
[QUOTE=azz]Can anyone share their results? (glx gears scores)[/QUOTE]

yep.

using the i915 module included in the 2.6.11 kernel, glxgears gave me about 450 fps.  (12.1", 1280x800, 1.7ghz, 855gme chipset)

i downloaded the latest i915 snapshot from that link you posted, switched to single user mode (important) and ran the install script.  since we're using xorg over here, i don't think we need the common snapshot.  i tried installing this and it just broke everything.  with the new i915 and drm modules loaded glxgears does ~830 fps.  big difference.  watching dvds and videos looks much smoother as well.

i'm wondering when (if ever) these drivers will be included in the kernel.  i'm also wondering why they're not and if there is a patch.

any questions about installing these just ask ... well i still have some myself actually.  the ones on intel's site are just really old versions of the one's on the dri site and they will not compile with ubuntu (or almost everything else i hear).

---

### Post by shof2k on 2005-06-20
Would you recommend the i915 module for an 845G chipset?   I have glxgears running at ~300 and there is definite room for improvement.  A good HOW-TO on this would be useful.

---

