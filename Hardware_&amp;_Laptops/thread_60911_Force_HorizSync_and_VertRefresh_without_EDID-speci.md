---
title: "Force HorizSync and VertRefresh without EDID-specified checking at xorg startup"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by adonias on 2005-08-29
Hi all. 

I have an AOC monitor with manual vertrefresh and horizsync values that are discarted and overlaped when i start x by the EDID-specified ones. Is there any way to force my values and/or disable this checking step? I knowthey are supported and correct because i found them in the monitor manual, and it's the only way to make my monitor reach the resolutions values that i have under windows when i choose to show all the resolution modes.

Regards.

(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 400 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 400 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 400 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(WW) NVIDIA(0): The user specified HorizSync "30.000-95.000" has been adjusted
(WW) NVIDIA(0):      to "30.000-70.000" (the intersection with EDID-specified
(WW) NVIDIA(0):      HorizSync "30.000-70.000")
(WW) NVIDIA(0): The user specified VertRefresh "50.000-160.000" has been
(WW) NVIDIA(0):      adjusted to "50.000-130.000" (the intersection with
(WW) NVIDIA(0):      EDID-specified VertRefresh "50.000-130.000"
(II) NVIDIA(0): AOC Spectrum: Using hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): AOC Spectrum: Using vrefresh range of 50.00-130.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(0): Not using mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using mode "1600x1200" (hsync out of range)

---

