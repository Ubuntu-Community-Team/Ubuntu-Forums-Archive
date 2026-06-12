---
title: "intel(82845G/) laptop, problems with fps and 3d acelerator"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by fidodido on 2005-10-26
Hello

I have a laptop (fujitsu siemens) AMILO L6825, it has intel(82845G) and a 15 tft monito, I tried with knoppix, suse9.2... (cdlive) with all this my resolutions was 640x480 and 60fps.

When I install ubuntu so I have problems with xorg, defaults xorg cannot work well with my video card and tft 15 monitor. I defined this values in xorg.conf and now I working with i810 driver and 1024x768 but i having problems with glxgears, and screensavers are very slowly. Looks like vesa driver, poor quality. 


--------------------------------------------------
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset In
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "fujitsusiements15"
        Option          "DPMS"
        HorizSync       30-61
        VertRefresh     56-76
EndSection
------------------------------------------------

- Are this values correct for 15" standar tft monitor?

HorizSync       30-61
VertRefresh     56-76
?

thanks

---

