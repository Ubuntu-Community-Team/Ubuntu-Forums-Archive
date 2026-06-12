---
title: "Can't set a custom resolution (I've added Modelines and edited xorg.conf)"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by Shiva_T on 2006-12-21
Hi,

I'm running Ubuntu Edgy, and have installed the NVIDIA proprietary drivers. However, they evidently aren't very functional, as the highest resolution option it gives me is 1280x720. I'm using a 1080p Samsung HDTV via DVI-HDMI, and it overscans quite a bit. So I have two problems:

1. I can't set the resolution higher than 1280x720, either through the NVIDIA Control Panel, or through the Screen Resolution setting.
2. At 1280x720 or even 800x600, the TV is overscanning like crazy.

What I'd really like to do is to set the resolution to 1768x992, which works perfectly in Windows and gives me a full, non-overscanned desktop.

I've made the following change to my xorg.conf file:

```
Section "Monitor"
    Identifier     "Samsung"
    HorizSync       32.0 - 79.0
    VertRefresh     59.0 - 79.0
    Option         "DPMS"
    Modeline "1768x992" 145.42  1768 1872 2064 2360   992  993  996 1027 +hsync +vsync
EndSection

Section "Device"
    Identifier     "7600GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "7600GT"
    Monitor        "Samsung"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1768x992" "1024x768"
    EndSubSection
EndSection
```

Still no luck; I don't see the 1768x992 mode under screen resolution. Any idea what might be wrong?

I really need to get this resolution working before I can start using my new Linux installation.

Thanks!

---

### Post by mbobak on 2006-12-21
There should be info in /var/log/X11.0.log, with messages explaining what the X server thinks is wrong w/ that particular modeline.

If you don't understand the error messages in the log, post the relevant portion here.

-Mark

---

### Post by Shiva_T on 2006-12-22
All it says is:

No valid modes for "1768x992"; removing.

which is weird, since I got those modeline timings from Windows, where they work fine. I tried the timings from the online generator, with no luck either.

---

