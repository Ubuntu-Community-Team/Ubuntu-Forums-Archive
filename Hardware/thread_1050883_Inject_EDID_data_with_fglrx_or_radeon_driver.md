---
title: "Inject EDID data with fglrx or radeon driver?"
date: 2009-01-26
forum: Hardware
---

### Post by dsm iv tr on 2009-01-26
Hi there,

I'm the 'proud' owner of a broken Viewsonic VX2240w. The funny thing here, though, is that it -came- broken: it doesn't have any EDID data at all, and as a result my machines don't allow it to run over 1024x768, which is really annoying on a widescreen monitor, for a web developer and programmer - and probably everyone else too.

```

...
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000003, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(EE) fglrx(0): Unknown EDID version 0
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Connected Display2: LCD on internal LVDS [lvds]
...

```

I've only been able to get a quasi-working solution with the fglrx driver, no other driver will run it at its native 1680x1050/60Hz. My current and not so great solution is adding this to xorg.conf:

```

SubSection "Display"
        ...
        Modes     "1680x1050_60.00" "1280x800_60.00"
        ...
EndSubSection

Section "Monitor"
        ...
        Modeline    "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
        Modeline    "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
        ...
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"

        Option      "HSync2" "24-82"
        Option      "VRefresh2" "50-75"

        Option      "DesktopSetup" "clone"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "OverlayOnCRTC2" "1"
        Option      "RenderAccel" "true"
        Option      "UseFastTLS" "0" # 2=compat | 1=faster | 0=fastest
        Option      "XAANoOffscreenPixmaps" "true"
EndSection

```

That's there for the benefit of people who might also have the same issue as me. This solution works OK about 25% of the time, but the other 75% of the time it leaves the monitor fuzzy and unreadable. Sometimes a reboot fixes it, sometimes it doesn't. Returning from DPMS (display) Sleep/Suspend also leaves it nearly unusable.

As luck would have it, I've found some EDID data for a monitor extremely close to my model (VX2235w) - and people with an nVidia card have reported using it with the "CustomEDID" directive in xorg.conf works quite well. I'll attach it in case anyone wants it.

Now to the meat of my question: I have a Radeon Xpress 200M. Is there a similar directive I can use with either the radeon or fglrx driver to load the EDID data I have in place of the null/gabrage data the monitor returns?

Meanwhile, I'm going to try translating some Modelines from a friend's copy of nVidia's "Control Panel" app...

Thanks!

---

### Post by dsm iv tr on 2009-01-26
The plot thickens.

[http://ati.cchtml.com/show_bug.cgi?id=789](http://ati.cchtml.com/show_bug.cgi?id=789)

I'm pretty sure it's still an EDID issue, though, because the stock ati/radeon driver also doesn't see the EDID data.

---

