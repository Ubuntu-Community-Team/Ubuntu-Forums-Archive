---
title: "Ubuntu jaunty not recognizing my ati graphics card driver."
date: 2009-09-25
forum: Hardware
---

### Post by samrap200 on 2009-09-25
Hi everyone. I'm new to ubuntu. I have an ATI Mobility Radeon HD 2300 Hypermemory graphics card which my ubuntu jaunty is not recognizing. Can anyone please tell me how to enable my graphics card on my system. thanx.

---

### Post by dagoth_pie on 2009-09-25
Does anything show up in "Hardware Drivers" under System/Administration?

---

### Post by danteuk on 2009-09-25
Anybody ever find a cure for this:
```

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
  compiled for 1.4.99.906, module version = 8.59.2
  Module class: X.Org Video Driver
[atiddxSetup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.4.-1.906
(II) UnloadModule: "fglrx"
(II) Unloading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)
(EE) No drivers available.

Fatal server error:
no screens found

```

I just installed the 9.3 ATI driver, now X won't start.
It seems to think X.org is 7.1 but synaptic tells me it's 7.4

Default original 'open' driver was no use at all once I turned on desktop effects. really screwed up display. Hence trying to install official ATI driver. 
This is an old laptop with a duff lcd so I'm connecting it to an external monitor. The GPU is old X300 thus I'm stuck with legacy driver 9.3 - that's if I can make it work.

```

Section "ServerLayout"
  Identifier     "aticonfig Layout"
  Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
  Identifier   "aticonfig-Monitor[0]-0"
  Option      "VendorName" "ATI Proprietary Driver"
  Option      "ModelName" "Generic Autodetecting Monitor"
  Option      "DPMS" "true"
EndSection

Section "Device"
  Identifier  "aticonfig-Device[0]-0"
  Driver      "fglrx"
  BusID       "PCI:1:0:0"
EndSection

Section "Screen"
  Identifier "aticonfig-Screen[0]-0"
  Device     "aticonfig-Device[0]-0"
  Monitor    "aticonfig-Monitor[0]-0"
  DefaultDepth     24
  SubSection "Display"
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

```

NOTE: ATI installer failed, useless piece of ... ( complained 'Error: ./default_policy.sh does not support version' )
So I used these instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start")

---

### Post by samrap200 on 2009-09-25
dagoth_pie,  sorry for the slow response, i was not anticipating such a quick reply,  no nothing shows under System/Administration/Hardware Drivers.....It states that it doesnt recognize any propriety drivers.

---

### Post by samrap200 on 2009-09-25
[http://wiki.cchtml.com/index.php/Ubu...fore_you_start](http://wiki.cchtml.com/index.php/Ubu...fore_you_start)   I already tried the aforementioned procedure on this page. It still could not recognize the driver.

---

### Post by dagoth_pie on 2009-09-25
The link you sent doesn't work, it's got a few dots in the middle. Check to make sure that the "linux-restricted-modules" package is installed

---

### Post by samrap200 on 2009-09-26
I just installed the linux-restricted-modules package from synaptic. No change.

---

