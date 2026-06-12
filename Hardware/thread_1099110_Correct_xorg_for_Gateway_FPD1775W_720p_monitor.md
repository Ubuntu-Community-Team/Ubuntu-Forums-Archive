---
title: "Correct xorg for Gateway FPD1775W 720p monitor"
date: 2009-03-17
forum: Hardware
---

### Post by Tulsapoke on 2009-03-17
I had meant to post the settings I finally got to work for my father-in-law's monitor.  Searching the forums I found several people with the same issue.  Here is the xorg I changed.

/etc/X11/xorg.conf

```
Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Unknown"
    ModelName      "Gateway FPD1775W"
    HorizSync       31.0 - 64.0
    VertRefresh     59.0 - 71.0
# 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
  Modeline "1280x720"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth      24
        Modes      "1280x720" "1024x768" "800x600"
    EndSubSection
EndSection
```

This enabled this monitor to work perfectly in native 720p resolution.  Hope this helps someone out.

---

### Post by Hoza85 on 2009-11-19
I just wanted to know what where the steps you took to configure your xorg for the Gateway FPD1775W 720P Monitor? I am a newb to Linux. I am actually trying to configure my friends complete system. Here's a link to my friends GatewayGT5418E spec's ([http://support.gateway.com/s/PC/R/1009445/1009445sp2.shtml](http://support.gateway.com/s/PC/R/1009445/1009445sp2.shtml))

---

