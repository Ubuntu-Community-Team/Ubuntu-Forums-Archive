---
title: "Getting QNIX QX2710LED monitor to work with nvidia drivers"
date: 2014-08-16
forum: Hardware
---

### Post by Vakz on 2014-08-16
So I have recently started tinkering with Linux, and still have a lot to learn. I've previously tried Fedora and LinuxMint, so at this point I'm pretty confident that it's not distro specific or whatever.

My current setup of monitors are a QNIX QX2710LED and a BENQ G2420HDBL. My graphics card is a GTX 670. With a clean install, both monitors work fine. However, when installing Nvidia drivers, it seems to be unable to configure the QNIX. Instead, the monitor will keep flashing different test screens. As far as I can tell from searching on Google, this is due to the screen giving invalid EDID info, which isn't very surprising since it's a very cheap monitor I got off of ebay. However, it seems the solution seems to be to write my own xorg.conf, as this appears to have solved the issue for either, but I feel that doing that is just way out of my league. I looked around on wiki.x.org, but in the end conceded that I'm just not getting it, and it would take a very long time to figure it out when I still have to google pretty much every command I do in Linux to make sure it's correct. I tried using some of the configs I found just as they were, but it's not really working, and even if they were, I assume some info would have to be added for my secondary monitor.

In Windows (where the setup works fine), the EDID info I'm able to pull is:

For the QNIX:
```

Registry Key             : DISPLAY\HYO049B\5&1c7e09a&0&UID1048848
Manufacture Week         : 40 / 2011
ManufacturerID           : 12067 (0x2F23)
ProductID                : 1179 (0x049B)
Serial Number (Numeric)  : 0 (0x00000000)
EDID Version             : 1.3
Display Gamma            : 2.20
Maximum Image Size       : 60 X 34 cm (27.2 Inch)
Maximum Resolution       : 2560 X 1440
Support Standby Mode     : No
Support Suspend Mode     : No
Support Low-Power Mode   : Yes
Support Default GTF      : No
Digital                  : Yes

Supported Display Modes  :
    2560 X 1440  60 Hz
```

For the BENQ:
```
Registry Key             : DISPLAY\BNQ785F\5&1c7e09a&0&UID1048851
Monitor Name             : G2420HDBL
Serial Number            : 68A00675SL000
Manufacture Week         : 34 / 2010
ManufacturerID           : 53513 (0xD109)
ProductID                : 30815 (0x785F)
Serial Number (Numeric)  : 21573 (0x00005445)
EDID Version             : 1.3
Display Gamma            : 2.20
Vertical Frequency       : 50 - 76 Hz
Horizontal Frequency     : 24 - 83 KHz
Maximum Image Size       : 53 X 29 cm (23.8 Inch)
Maximum Resolution       : 1920 X 1080
Support Standby Mode     : No
Support Suspend Mode     : No
Support Low-Power Mode   : Yes
Support Default GTF      : No
Digital                  : Yes

Supported Display Modes  :
     720 X  400  70 Hz
     640 X  480  60 Hz
     640 X  480  75 Hz
     800 X  600  60 Hz
     800 X  600  75 Hz
     832 X  624  75 Hz
    1024 X  768  60 Hz
    1024 X  768  75 Hz
    1152 X  720  60 Hz
    1280 X  720  60 Hz
    1280 X  960  60 Hz
    1280 X 1024  60 Hz
    1280 X 1024  75 Hz
    1600 X  900  60 Hz
    1680 X 1050  60 Hz
    1920 X 1080  60 Hz

```

---

### Post by grahammechanical on 2014-08-16
Have you tried the Nvidia Xserver settings manager? It is installed when we install a Nvidia driver. That may allow you to select the screen resolution.

---

### Post by Vakz on 2014-08-17
nvidia-settings unfortunately seems very limited. In Basic mode, all it offers is 800x600 (which doesn't work). In advanced mode, I can enter 2560x1440 as ViewPortIn, but not as ViewPortOut (when I unfocus the line to click Apply, it goes back to 800x600+0+0).

---

