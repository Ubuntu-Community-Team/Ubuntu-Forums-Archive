---
title: "ATI driver - xorg mismatch - in 9.04"
date: 2009-09-26
forum: Hardware
---

### Post by danteuk on 2009-09-26
Anybody know a solution to this:
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

NOTE: if I set xorg.conf back to use 'ati' then KDE crashes ( kwin actually ) I'm guessing it a problem with the libopengl that the ati driver installed, no idea how to get that back working again. So switched XFCE desktop to post this :)

---

### Post by ssri on 2009-09-26
From the looks of things, you might have tried to install ATI's Proprietary drivers for an unsupported card.  Several months ago, ATI relegated a bunch of cards (some merely 1.5 years old) to legacy status, meaning that last Catalyst Driver that supported those cards was version 9.3.  Unfortunately, Jaunty's xorg-xserver only supports Catalyst version >9.4.  So, unless you want to downgrade xserver to Intrepid's version ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)), then you have to use the opensource drivers if your ATI card is <=x19xx.  There's a ton of threads detailing how to do so.

---

### Post by danteuk on 2009-09-26
Exactly right, my card is not supported by the latest driver so I'm trying to use 9.3 - I'll look into downgrading xorg, failing that I just have to wait for the open driver to improve :(

---

### Post by danteuk on 2009-09-26
I down graded my xorg to the one from intrepid and installed the 9.3 driver.
Now X starts okay but fglrx is not working I think.

$ fglrxinfo
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13

I when I created the .deb files from the ati installer ( 9.3 ) I used this line:
sh ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty 

Maybe I should use specific Ubuntu/intrepid instead?
or is there maybe something else wrong.


UPDATE: Ignore me - I needed to downgrade/install libdrm2=2.3.1-0build1

---

