---
title: "Latest 'radeon' driver: do you know of a repository?"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by tribaal on 2006-11-01
Hi all!

I have successfully upgraded to edgy (fresh install), and love the new features, especially the new Xorg. It allowed me to use the radeon open source drivers for my ATI m300 card, and still get beryl to run :)

Being an upgrade junkie however, I would love to always be updated on the newest-badest version of the open radeon driver, to match my automatic Beryl CVS version... I know this opens the door to many potential problems, but I backup often and loke the bleeding-edge feeling...

So does anybody know of an unofficial repository for Xorg's radeon Drivers? (Or maybe Xorg as a whole?)
If not, maybe could someone point me out a comprehensive guide to compiling the latest radeon drivers by hand? I can't even seem to find the xorg radeon driver's "homepage" or main project page on the net... :(

Thanks a lot!

- trib'

---

### Post by toaste on 2006-11-01
I haven't heard of a repo, but a good bit of the information available on this driver is at [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) although I believe it's currently maintained with Xorg.

Speaking of the r300 driver, how'd you get it the dang thing to load?  I've tried to set up my xorg.conf file to load the radeon driver to get DRI and AIGLX working, but it falls back to the 'ati' driver and software rendering.  Mobility Radeon 9600, upgraded from Dapper to Edgy recently...

---

### Post by tribaal on 2006-11-02
Well here's my revelant section of xorg.conf, hope this will help you...

Section "Device"
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver          "radeon"
        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "EXA"
        Option "XAANoOffscreenPixmaps" "true"
        Option "RenderAccel" "true"
        Option "AGPMode" "4"
        Option "AGPSize" "64"
        Option "AGPFastWrite" "true"
        Option "backingstore" "true"
        Option "AllowGLXWithComposite" "true"
        Option "SubpixelOrder" "NONE"
        Option "DynamicClocks" "true"
        Option "bioshotkeys" "true"
        BusID           "PCI:1:0:0"
EndSection


Cheers!

- trib'

---

