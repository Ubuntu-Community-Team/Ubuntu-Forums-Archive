---
title: "graphics drivers..."
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by skolly123 on 2008-01-26
I am running ubuntu on my Acer Aspire 3630, everything mostly works all good, but when i was trying to run Unreal Tournament 2004, the splash-screen comes up, then this error appears:

>Xlib:  extension "XFree86-DRI" missing on display ":0.0".
>WARNING: ALC_EXT_capture is subject to change!
>Couldn't set video mode: Couldn't find matching GLX visual
>
>
>History: 
>
>Exiting due to error

anyone know what this means and how to fix it?

this is in xorg.conf, dunno if this helps...
>Section "Device"
>	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
>	Driver		"sis"
>	BusID		"PCI:1:0:0"
>EndSection

any help at all would be extremely appreciated, as I am not too knowlegable about graphics and drivers and stuff...

---

### Post by overdrank on 2008-01-27
> **skolly123 said:**
> I am running ubuntu on my Acer Aspire 3630, everything mostly works all good, but when i was trying to run Unreal Tournament 2004, the splash-screen comes up, then this error appears:

>Xlib:  extension "XFree86-DRI" missing on display ":0.0".
>WARNING: ALC_EXT_capture is subject to change!
>Couldn't set video mode: Couldn't find matching GLX visual
>
>
>History: 
>
>Exiting due to error

anyone know what this means and how to fix it?

this is in xorg.conf, dunno if this helps...
>Section "Device"
>	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
>	Driver		"sis"
>	BusID		"PCI:1:0:0"
>EndSection

any help at all would be extremely appreciated, as I am not too knowlegable about graphics and drivers and stuff...

HI and welcome, I do not believe that the SIS graphics are not supported well in linx and you may look here. [http://ubuntuforums.org/showthread.php?t=347451](http://ubuntuforums.org/showthread.php?t=347451)

---

