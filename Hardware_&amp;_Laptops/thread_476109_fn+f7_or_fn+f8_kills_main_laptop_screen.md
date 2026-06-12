---
title: "fn+f7 or fn+f8 kills main laptop screen"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by enortham on 2007-06-16
The buttons fn+f7 and fn+f8 for increasing and decreasing the brightness on my hp dv6000 laptop cause the main laptop screen to go completely black on my dual monitor setup. The other external LCD screen continues to work fine however. The screen goes completely black after hitting fn+f6 or fn+f7 for the first time. If I restart gdm via ctrl+alt+bkspace the screen is actually brighter or dimmer so the keys appear to be working I just am not sure why the screen dies. I have a built-in intel card.

Here's the Device section of my xorg.conf
```

Section "Device"
        Identifier      "0 Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          0
        Option          "MonitorLayout" "CRT,LFP"
        Option          "DRI" "false"
EndSection

Section "Device"
        Identifier      "1 Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
        Option          "MonitorLayout" "CRT,LFP"
        Option          "DRI" "true"
EndSection

```

Here's the ServerLayout section of my xorg.conf
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "0 Screen"
        Screen          1 "1 Screen" RightOf "0 Screen"
        Option          "Xinerama" "on"
        Option          "Clone" "off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

Anybody know a way of fixing this problem?

Eric

---

