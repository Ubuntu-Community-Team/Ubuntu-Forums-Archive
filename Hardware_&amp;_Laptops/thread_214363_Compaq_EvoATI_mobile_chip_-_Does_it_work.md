---
title: "Compaq Evo/ATI mobile chip - Does it work?"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by aztektum on 2006-07-12
I've dug around on the forums and can't seem to find a clear cut answer to something I have heard. Do the ATI drivers work on laptops with (somewhat) older Radeon chips? Specific to my case, I have a Compaq EVO n600c that Windows use to show having a Radeon 9000 mobile chip.

I did the install and basic setup stuff, but no joy. I'm just wondering if it's worth tinkering with further or not.

Thanks

---

### Post by rs3 on 2006-07-13
I have a Presario of around the same age with a subpar video chip (8MB Radeon Mobility M6 LY).  When I installed Dapper on it, xorg defaulted to the ATI driver, which resulted in garbage/noise over buttons and infrequent hard freezes; these could be resolved by switching to the VESA driver (ugh) or by reverting to Breezy and its older X.org (and driver set).

But, yeah, the bundled, open-source ATI drivers should work.  The FireGL drivers available from ATI did not work for me--but your chip appears to be newer (or, at least, offer 16 or 32MB of video memory versus my meager 8MB) and so your mileage may vary.

Good luck

---

### Post by indigoshift on 2006-08-08
I'm getting the weird garbage over the buttons in the windows on my N600c as well, but (fortunately) no hard freezes.

Could you point me in the direction of these open-source ATI drivers?  I'd appreciate it.  Thanks!

---

### Post by Eddie Hung on 2006-08-10
Hello everyone!

I have a Compaq n410c with a similar video card, and I'm using the 'radeon' driver under xorg.conf - and I am seeing corruption on my buttons too. I've tried the 'ati' driver and that doesn't seem to do anything for me...

I can also tell you our graphics card won't work with the ATI proprietary drivers, so the open source Xorg drivers is our only choice!

Good luck!

Eddie

---

### Post by kronepils on 2006-08-10
I have a Radeon Mobility M7, and I'm using the radeon driver. But there is no difference between the ati and the radeon driver. Not if the chip supports it, that is. The ati driver is choosing the radeon driver if the card supports it.
I have the garbage on my buttons aswell with X.org. Instead I use X.org-air (AIGLX). With that I can use compiz (nice) and metacity without problems!

Add this to your /etc/apt/sources.list:
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

---

### Post by Papa-san on 2006-08-12
OK... So a bunch of us have this problem... I don't see where the solution is. Can anyone help with finding/ installing the right drivers? I have no clue as to what to do next... The hard crashes are tough to deal with. (Especially after bragging to my son about how stable my Breezy was... He's HARDCORE winxp...)

---

### Post by Eddie Hung on 2006-08-15
I have a Mobility M6 LY and Compiz and Gnome (regardless of XGL or AIGLX) results in the 'half screen problem' (see [http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#Half-screen_problem)](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#Half-screen_problem))... which is terribly unfortunate =(

I don't particularly want to edit the source and recompile the whole thing, as it suggests, and I'm hoping it'll get fixed soon!

Eddie

---

### Post by gustl87 on 2006-08-16
hello

i am using an ati m6 - and i got the same strange freezes.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "ati" and if freezing continues, you might edit it as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

---

### Post by Eddie Hung on 2006-08-21
I've got all the performance tweaks turned on, and I'm having no problems with my Radeon M6 LY (built into a Compaq N410c laptop).
EDIT: By performance tweaks, I mean the xorg parameters described here: [http://ubuntuforums.org/showthread.php?t=221672](http://ubuntuforums.org/showthread.php?t=221672)

I've now found the solution to my half screen compiz problem above: I believe you need to set the AGPSize variable manually inside xorg.conf for it to work correctly.

This is for AIGLX and Compiz, but I have uninstalled both them packages so I won't be able to confirm this for sure until I reinstall them again in Edgy.

Eddie

---

