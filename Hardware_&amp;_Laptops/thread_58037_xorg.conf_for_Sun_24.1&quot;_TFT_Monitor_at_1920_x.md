---
title: "xorg.conf for Sun 24.1&quot; TFT Monitor at 1920 x 1200"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by birju on 2005-08-18
Hi,
After much playing, experimenting, googling and forum searching, after 3 days I've managed to get my Sun 24.1" Monitor running at 1920x1200!
Here is the relevant section from the xorg.conf file if you are interested:
```

Section "Monitor"
        Identifier "Monitor0"
        VendorName "Sun Microsystems"
        ModelName "Sun 24-inch"
        HorizSync 30-82
        VertRefresh 56-76
        Modeline "1920x1200" 151.2 1920 1928 1992 2056 1200 1202 1206 1234 -HSync +VSync
        Option "dpms"
EndSection

```
You might want to change that Monitor0 bit to "Generic Monitor" or something.
Cheers,
Birju

---

### Post by antares727 on 2008-02-23
):P
Thank you for your post -- I just reconfigured my xorg.conf file per the settings given. I did change my "screen" section to track with the new monitor and added the 1920x1200 resolution to the 'mode' section.

Rebooting the system brought up the system with the 1920x1200 resolution without any errors or issues.

---

