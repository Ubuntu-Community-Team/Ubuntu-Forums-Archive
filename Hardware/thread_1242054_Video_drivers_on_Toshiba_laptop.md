---
title: "Video drivers on Toshiba laptop"
date: 2009-08-16
forum: Hardware
---

### Post by cosmicd on 2009-08-16
I'm having a Thosiba Satelite laptop. 

lshw gives me the next information: 

```
description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller

```So, my question is how can I understand whether the drivers for this graphic controller are installed or not ? 


/etc/X11/xorg.conf :

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection

```

---

