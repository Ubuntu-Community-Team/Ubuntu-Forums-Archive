---
title: "Xgl/Compiz broke after Ibex upgrade"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by nixscripter on 2009-03-17
Hello everyone.

I just upgraded to Ibex from Gusty (going through Hardy) on a Dell Inspiron 1402n. I had Compiz working using Xgl before, but after a **dpkg-reconfigure xserver-xorg**, it doesn't work anymore -- even after I put my old Xorg.conf file back.

The video card is an Intel Mobile 965M. Ibex just upgraded the driver (xserver-xorg-video-intel) to version 2:2.4.1-1ubuntu10.3

The relevant part of Xorg.conf is:

```
Section "Device"
        Identifier      "Improved Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "DRI"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "PageFlip"      "true"
        Option          "TripleBuffer"  "true"
        Option          "FramebufferCompression"        "true"
EndSection
```

But since running the dpkg-reconfigure, I get this in Xorg.log:

```
(WW) intel(0): Option "AllowGLXWithComposite" is not used
```

That option was how I got compiz to work before. Did this happen because of the driver upgrade?

When I run compiz, I get:

```
Checking for Xgl: present.
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
```

And then it dies.

When I run compiz on display :0 (which the video card is driving directly), everything goes black, and has serious redrawing issues.

How can I fix this problem?

---

