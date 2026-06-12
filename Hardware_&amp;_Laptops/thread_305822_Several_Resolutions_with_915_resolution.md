---
title: "Several Resolutions with 915 resolution"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by mexlinux on 2006-11-24
Hi:
I have 915resolution working very good, and I work on 1280x800.

But that is the only resolution available in the System Settings options.

How can I add another resolution so my wife can switch if she wants loger resolution?

Thanks

---

### Post by Mruva on 2006-11-24
You must edit your /etc/X11/xorg.conf
In section Monitor insert correct values HorizSync and VertRefresh of yours monitor, for example: 
Section "Monitor"
  Option       "CalcAlgorithm" "XServerPool"
  HorizSync    31-64
  Identifier   "Monitor[0]"
  ModelName    "1280X1024@60HZ"
  Option       "DPMS"
  VendorName   "--> VESA"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection

---

### Post by Mruva on 2006-11-24
ooops, i forgot, in section Screen you must insert resolution values, for example:
Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

---

