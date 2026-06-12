---
title: "Can't set native resolution (i865G + wide-screen LCD)"
date: 2008-11-30
forum: Hardware
---

### Post by muzzz on 2008-11-30
I originally posted the following on kubuntuforums.net a week ago, without getting any replies. I'm hoping someone here will be able to shed some light on the issue.

I've recently installed 8.10 on my desktop, which has an intel 865G graphics controller and a wide-screen monitor. So far, I've been unable to convince X to use my monitor's native 1280x768 resolution. The closest I've gotten is with this xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       47.73
        VertRefresh     60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

        SubSection "Display"
                Depth   24
                Modes   "1280x768"
        EndSubSection
EndSection
```

Strangely, this causes X to go into 1360x768 mode, which my monitor doesn't even support according to its documentation.

I've had problems with intel graphics controllers and resolutions in the past. Apparently, their video BIOSs are notorious for incorrectly reporting the modes they support. In previous versions of kubuntu, I've succesfully used the 915resolution tool to work around this problem. Unfortunately, it seems that 915resolution is no longer available in 8.10. A quick googling tells me that it's been obsoleted:

 *"The 915resolution package becomes obsolete with the newer xorg, especially if you have the xserver-xorg-video-intel package installed. Newer xorg brings modesetting support by default."*

The only other suggestion I've fouind was running dpkg-reconfigure xserver-xorg. But when I try that, the only display-related prompt I get asks whether or not I want to use the framebuffer interface. In the end, it outputs an absolutely minimal xorg.conf configured to use the "vesa" driver.

I'm at a complete loss now. Any help in getting my native resolution back would be greatly appreciated.

---

