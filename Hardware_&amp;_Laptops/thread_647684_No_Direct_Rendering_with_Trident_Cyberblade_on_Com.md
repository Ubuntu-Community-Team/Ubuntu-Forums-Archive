---
title: "No Direct Rendering with Trident Cyberblade on Compaq Presario"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by alienjon on 2007-12-22
A while back I inherited a Compaq Presario 1200 and installed Ubuntu on it. The one thing that really bugs me about it is that I'm not getting any direct rendering from the video card.  I don't know the specific specs of the card (I will share what I know in a moment) but I do know that before I installed Ubuntu, XP was installed and I was able to play Dungeon Keeper 2 with a little lag (so I know that the card should be capable of 3D rendering even if it isn't that great)  Here's what I can say:

```
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade i1 (rev 6a)
```

```
XLib: extension "XFree860-DRI missing on display ":0.0".
Screen 0: not direct rendering capable.
```

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

```
Section "Module"
   Load   "glx"
   Load   "dri"
EndSection

Section "Device"
   Identifier   "Trident Microsystems CyberBlade i1"
   Driver   "trident"
   BusID   "PCI:1:0:0"
EndSection

Section "DRI"
   Mode 0666"
EndSection
```

I have also tried commenting out `Load  "dri"` and the entire "DRI" section and when I do, I get the following:

```
direct rendering: No (If you want to find out why, try setting {yadda yadda...}
server glx vendor string: SGI
```

The change is that I'm not using mesa any more but SGI (not sure what that is, exactly, or if this means I'm in a step in the right direction) but things still aren't working as I hoped.  If it is a matter of trident drivers not being very well supported (or at least for my card) then thats ok, but I'm not settled with the idea that it's just an OLD card that can't do 3D graphics because I was able to get them in Windows.

---

### Post by nickmcg on 2008-01-08
There are pleny of threads about the trident boards - it would appear that there was a driver for xfree86 which did have 3d acceleration, but that seems to be what was ported to xorg.
It seems that the main reason for the lack of an accelerated driver is that the spec was never fully released

Nick

---

