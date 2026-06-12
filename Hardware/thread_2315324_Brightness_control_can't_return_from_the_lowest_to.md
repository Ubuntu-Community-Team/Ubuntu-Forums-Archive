---
title: "Brightness control can't return from the lowest to higher levels."
date: 2016-02-27
forum: Hardware
---

### Post by francedraguignan on 2016-02-27
Several days ago I tried to fix a quite popular problem. In my notebook the brightness control keys weren't working. I have added a file [COLOR=#DDDDDD][FONT=monospace][/FONT][/COLOR][FONT=monospace]/usr/share/X11/xorg.conf.d/20-intel.conf[/FONT][COLOR=#DDDDDD][FONT=monospace]
[/FONT][/COLOR]with following content: 
[FONT=arial][SIZE=2]Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection

[COLOR=#000000]Now I can adjust the brightness, but every time when I reach the lowest brighness possible - it gets blocked and I cannot return to a higher level of brightness.
Have you encountered a similar problem? My computer is Samsung NP-R509.  [/COLOR][/SIZE][/FONT]

---

