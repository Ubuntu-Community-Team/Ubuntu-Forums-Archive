---
title: "how to add a new resolution to system-&gt;preferences-&gt;resolution ?"
date: 2008-12-03
forum: Hardware
---

### Post by hecato on 2008-12-03
Hello there, my  graphic card is nvidia

so xrandr output:

```
Screen 0: minimum 1280 x 800, current 1280 x 800, maximum 1280 x 800
```

So that is, I need add 800x600 because I need to put a presentation of openoffice to the external output of the lap.


So what I need to add?

---

### Post by tjandracom on 2008-12-03
try to edit file /etc/X11/xorg.conf

you can add the resolution you want in SubSection "Display" -> Modes. 
it should looked like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel 82810E"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by hecato on 2008-12-03
Hi there theproblem stand and still, I need help beucase I do my presentation in about 4 hours!, so plz help.

I have added the modes to the screen, however, ehre is a part of the Xorg log

```

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.50.00.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600M GT at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "640x480"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

```



Edit

My laptop is a vostro 1500 with NVIDIA 8600, driver installed in the automatic way and they work OK I have 3D accel.

---

