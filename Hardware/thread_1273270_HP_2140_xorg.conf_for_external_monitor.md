---
title: "HP 2140 xorg.conf for external monitor"
date: 2009-09-23
forum: Hardware
---

### Post by jambel on 2009-09-23
> Hi, 

does anyone knows how to configure my xorg.conf to connect HP 2140 to an external monitor?

When I did it the only resolution I have is 800x600 in a wide screen.

Configuration:
Ubuntu 9.04 + HP 2140ok I fix it by adding

```
Section "Device"
    Driver "intel"
EndSection
```and```
SubSection "Display"
    Modes "1680x1050" "1440x900" "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
```

---

