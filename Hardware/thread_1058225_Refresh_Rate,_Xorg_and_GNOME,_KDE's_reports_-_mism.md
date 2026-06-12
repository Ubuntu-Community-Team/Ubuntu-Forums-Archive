---
title: "Refresh Rate, Xorg and GNOME, KDE's reports - mismatch."
date: 2009-02-02
forum: Hardware
---

### Post by sktrad_ on 2009-02-02
Since installing 8.10, I uninstalled ubuntu's packaged nvidia drivers, headed to nvidia's site and - having downloaded the latest drivers - I manually installed them.

Having acknowledged everything worked, I wished to fine tune a few things.

I check the refresh rate in "nvidia-settings" and noticed it read "60", I sudoed and saved a new xorg file where I specified a "75" refresh rate, with the same "nvidia-settings" utility. The "xorg.conf" now includes the following section:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

... as well as:

```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX922"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

```

I then loaded both "gnome-control-center" and KDE's "system-settings" only to find out that both reported a 50 and 51 Hz refresh rate. How can I tell the actual refresh rate, and why do these different utilities not report the same data.

---

### Post by sktrad_ on 2009-02-04
I might add - @50Hz vertical refresh rate, I really think I may notice a flicker, which I don't, as it is. Yet both KDE and Gnome report that 50Hz refresh rate, and only offer a change to 51 ...

---

