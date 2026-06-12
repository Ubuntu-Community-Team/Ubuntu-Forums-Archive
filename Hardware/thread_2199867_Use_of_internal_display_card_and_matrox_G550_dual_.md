---
title: "Use of internal display card and matrox G550 dual head (three monitors)"
date: 2014-01-16
forum: Hardware
---

### Post by FixFax on 2014-01-16
Hello!
I've just dumped my old Windows XP installation and installed Ubuntu 13.10 on my desktop PC.
Now I can start work at home office again (the last year only ubuntu laptops are used).
Anyway, I am still a ubuntu newbe! For sure!
I want to reuse my Matrox G550 PCIe 1x FLH60 (with two HPw19 DVI monitors) on top of my main display on internal card.
I have searched through forums for days, but still are stucked with the main Samsung SyncMaster 2494HM on internal HDMI or VGA (both works (one at a time)).

lcpci shows:
[COLOR="#FF0000"]00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
03:00.0 VGA compatible controller: Matrox Electronics Systems Ltd. Millennium G550 (rev 01)[/COLOR]

I have tried to establish several xorg.conf, the latest:

[COLOR="#FF0000"]Section "Device"
Identifier "Matrox G550-1"
Driver "mga"
BusId "PCI:3:0:0"
EndSection

Section "Device"
Identifier "Matrox G550-2"
Driver "mga"
BusId "PCI:3:0:0"
EndSection

Section "Monitor"
Identifier "Monitor 1"
Option "DPMS"
HorizSync 30-75
VertRefresh 30-60
EndSection

Section "Monitor"
Identifier "Monitor 2"
Option "DPMS"
HorizSync 30-75
VertRefresh 30-60
EndSection

Section "Screen"
Identifier "ScreenTopLeft"
Device "Matrox G550-1"
Monitor "Monitor 1"
DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "Screen"
Identifier "ScreenTopRight"
Device "Matrox G550-2"
Monitor "Monitor 2"
DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "ServerLayout"
Identifier "Multihead"
Screen "ScreenTopLeft"
Screen "ScreenTopRight" RightOf "ScreenTopLeft"
# Screen "ScreenRight" LeftOf "ScreenLeft"
# Screen "ScreenRight2" RightOf "ScreenRight"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "ServerFlags"
Option "xinerama" "true"
Option "DefaultServerLayout" "Multihead"
EndSection[/COLOR]

At last i tried to establish xorg.conf step by step, but even the xorg.conf like below failed:

Section "Device"
Identifier "Matrox G550-1"
Driver "mga"
BusId "PCI:3:0:0"
EndSection

Anyone that can give me a "how-to" from A to Finish?

Best regards!

---

### Post by FixFax on 2014-03-17
Bump?
I am so used to use more than one monitor that I soon have to go back to use Windows 7 on host, just to have my three monitors working!
Pls help!!

---

