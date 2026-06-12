---
title: "Lenovo T400 - Two displays?"
date: 2008-10-25
forum: Hardware
---

### Post by fongandrew on 2008-10-25
I have a Lenovo T400 with a 1440x900 display and the Intel X4500 integrated graphics. After installing the 8.10 RC, the resolution seemed pretty low so I hopped into the Screen Resolution settings to change it.

In the Monitor Resolution Settings window, the Mirror Screens options was checked and the resolution maxed out at 1360 x 768. When I unchecked that however, I found that there were two displays in the settings. One is labeled Laptop 14" and has a max resolution of 1440x900. The other is labeled Unknown and has a max resolution of 1360 x 768.

That's really strange since I don't have any displays hooked up to the laptop.

Anyhow, I set the Unknown display's resolution to "Off", restarted GDE, and everything was fine, but I'm perplexed as to why that Unknown display with the 1360x768 resolution was there to begin with. Any suggestions?

My Xorg.conf -- pretty standard I think

Section "Monitor"
     Identifier      "Configured Monitor"
EndSection

Section "Screen"
     Identifier      "Default Screen"
     Monitor        "Configured Monitor"
     Device          "Configured Video Device"
EndSection

Section "Device"
     Identifier      "Configured Video Device"
EndSection

---

### Post by flintmecha on 2009-01-14
I have the same problem with my T400, and I'm using Arch Linux (Google led me here).

Bumping for answers.

---

