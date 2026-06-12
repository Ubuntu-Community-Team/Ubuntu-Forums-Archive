---
title: "Another ATI dual monitor problem X1800"
date: 2009-03-24
forum: Hardware
---

### Post by blacklocist on 2009-03-24
Hi All,

I have been working away on trying to enable dual monitors on my system. My video card is ATI Radeon X1800. I know dual monitor works with the card and works in Windows just fine. I am running latest ATI drivers 8.54.3 and Catalyst Control Center 2.1 (downloaded from ATI about a hour ago).

To best explain I decided to take screen shots. I have tried to mess with the xorg file but kept having X11 crash and return to xorg backup.

[IMG]http://www.mr337.com/Pictures/1.png[/IMG]

It asks to reboots so I do. On reboot I get a Out Of Range on my second monitor. Then it goes back to cloned screens, the CC shows it also.

[IMG]http://www.mr337.com/Pictures/2.png[/IMG]

WTF??? WTF????


Here is my current xorg.conf, I have not tweaked this any (have in the past and broke X11). Help? I also am using two Viewsonic VX924 if that helps.


Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
Option "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
EndSection

---

### Post by khelben1979 on 2009-03-24
If you have an DVI to VGA converter you can always try that to see if the ATi Catalyst can accept this instead, perhaps?

Other than that: are these 2 monitors identical in it's technical specifications?

*It wouldn't surprise me if the ATi Catalyst in this version has a serious bug which causes your problem b.t.w.*

---

### Post by blacklocist on 2009-03-24
Both of the lcds are running DVI. I don't have any converters :(

Also both monitors are identical. Even bought them at the same time. 


> **khelben1979 said:**
> If you have an DVI to VGA converter you can always try that to see if the ATi Catalyst can accept this instead, perhaps?

Other than that: are these 2 monitors identical in it's technical specifications?

*It wouldn't surprise me if the ATi Catalyst in this version has a serious bug which causes your problem b.t.w.*

---

