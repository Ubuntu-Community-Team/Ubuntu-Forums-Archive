---
title: "Force widescreen resolution w/nVidia binary?"
date: 2010-09-02
forum: Hardware
---

### Post by immerohnegott on 2010-09-02
So, I've cobbled together a system for use in the living room based around an nVidia 7950 GT. This is connected to my LCD TV via a DVI-VGA converter. For whatever reason, it refuses to let me force the native resolution of 1360 x 768 @ 60hz. I added a modeline to xorg.conf using the specs listed in the TV's service manual, and forced EDID off while I was at it.

The modeline is as follows: 

```
Modeline "1360x768@60" 84.52 1360 1392 1712 1744 768 783 791 807
```

This causes it to output 1360 x 768 (according to Xorg.0.log). 

```
(II) Sep 02 13:36:07 NVIDIA(0): Virtual screen size determined to be 1360 x 768
(**) Sep 02 13:36:07 NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option 
(**) Sep 02 13:36:07 NVIDIA(0): Enabling 32-bit ARGB visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Sep 02 13:36:07 NVIDIA(0): Initialized GPU GART
(II) Sep 02 13:36:07 NVIDIA(0): Setting mode "1360 x 768"
```

No errors are reported in the log, as far as I can see.

The output appears on the screen at 1024 x 768 (according to the TV), but is mushed so that it would look normal, albeit fuzzy, if stretched to 1366. 

This setup worked before a couple years ago (I had the same card e in a different machine running 8.04), though with a lot less hassle.


-----------------------------------------------------------
SOLVED
-----------------------------------------------------------

Used gtf to generate a pretty generic modeline, which at least displayed it in widescreen, though the image was stretched waaaay off the sides. Messed around with the modeline a bit to manipulate the image, and now it fits perfectly.

---

