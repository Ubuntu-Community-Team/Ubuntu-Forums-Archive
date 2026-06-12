---
title: "ATI Hybrids graphic card"
date: 2012-11-02
forum: Hardware
---

### Post by Rollback91 on 2012-11-02
Hi guys, 
i'm new in the forum and i'm sorry to be bothering you about this problem i've.
So i've bought a pc with 2 graphic cards ATI and im using the fglrx driver.

lspci | grep VGA 

```
 01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series] (rev ff)

```So when i use the integrated card (the first one) i've no problems, but if i want to switch to the dedicated one the graphic interface will not boot.
Ill post my xorg.conf for the integrated

```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```and this it the one i use for the dedicated:

```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Sorry for the bad english and for bothering you but im trying to fix this problem from weeks.

---

### Post by Bashing-om on 2012-11-02
Rollback91; Hi ! Welcome to the forum.

I am aware that there exist issues in switching graphic cards, but, I have no direct experience in same.

These links may provide some insight and workarounds:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://linux-hybrid-graphics.blogspot.com/2011/06/hybrid-graphics-linux-on-samsung-sf310.html](http://linux-hybrid-graphics.blogspot.com/2011/06/hybrid-graphics-linux-on-samsung-sf310.html)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

Post back with additional queries and let us know what works
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by Rollback91 on 2012-11-02
Thank you for the reply Bashing-om!
I've looked at the links you posted, but they say to use vga_switchero which is a tool that can be use just with the open source driver.
I've a problem with those driver:

1. my pc gets as hot as hell(also runing in not graphic mode, i don't know why, maybe some strange loop).

2. the 3d performance are not as good as they should.

I've tryed to change the PCI address of the dedicated card in the xorg.conf file like this:

```

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:2:00.0"
EndSection


```and now the system boots up, but im just able to use Unity 2D and when i give fglrxinfo i get:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```and when i run amdcccle i get:

```
There was a problem initializing Catalyst Control Center Linux edition. The causes may be as follows.

Without an installed graphics driver, or the driver AMD AMD does not work properly.

Please install the AMD driver appropriate for your AMD hardware or configure it using anticonfig.  p, li { white-space: pre-wrap; }
```If you know a way to turn the integrated graphic card off, i can try to install again the ATI driver and see if they will make my dedicated card work as it should!

thank you for the help!

---

