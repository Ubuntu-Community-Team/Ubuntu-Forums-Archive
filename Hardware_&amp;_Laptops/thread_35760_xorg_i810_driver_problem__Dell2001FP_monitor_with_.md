---
title: "xorg i810 driver problem : Dell2001FP monitor with i915 card (Dell Dimension D610)"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by edoardo on 2005-05-20
When my Dell Dimension D610 is attached to the Dell2001FP lcd screen, 
I can't use the i810 xorg driver that's most appropriate for my  i915GM chipset

the i810 driver is ok when using the internal 1400x1050 screen (although I need to run the 915resolution workaround [http://www.geocities.com/stomljen/)](http://www.geocities.com/stomljen/)).

But when using the external 1600x1200 screen, I have to edit xorg.conf and "downgrade" the driver to vesa.

With the i810 driver the screen comes up in 640x480 and the Xorg log says:

(1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 160MHz
(1400x1050,Generic Monitor) mode clock 100000MHz exceeds DDC maximum 160MHz

I guess that xorg.conf could be tweaked to convince xorg to use the mode at a good clock but I don't know how. 
any ideas ?
here's a snippet of my xorg.conf:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
#HorizSync 31.0 - 80.0
#VertRefresh 56.0 - 76.0
EndSection

Section "Device"
Identifier "Intel Corporation Intel Default Card"
#Driver "i810"
Driver "vesa"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Intel Default Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 8
Modes "1600x1200""1400x1050"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200""1400x1050"
EndSubSection
...

---

