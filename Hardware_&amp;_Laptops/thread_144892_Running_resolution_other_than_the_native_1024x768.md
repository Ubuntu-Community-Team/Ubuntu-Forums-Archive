---
title: "Running resolution other than the native 1024x768"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by pdobrev on 2006-03-15
Hello there!
I have a DELL Latitude D510 laptop with i810 video card. I was wondering if X can run in resolutions other than the native 1024x768 because no matter what I put in xorg.conf, it always launches in 1024x768.

Thanks.

---

### Post by slavik on 2006-03-15
for me, on my laptop with a screen with antive resolution of 1280x768, once I installed the ATI drivers, that is the resolution that X has been using :)

---

### Post by pdobrev on 2006-03-15
Well, I have no problems running X at the native resolution. The problem is that I want to use other resolutions as well in order to play games that run in non-native resolution in fullscreen mode.

---

### Post by pdobrev on 2006-03-18
These lines in /etc/X11/xorg.conf solved my problem:
Section "Monitor"
        Identifier      "Generic Monitor"
[B]        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
[/B]        Option          "DPMS"
EndSection

---

