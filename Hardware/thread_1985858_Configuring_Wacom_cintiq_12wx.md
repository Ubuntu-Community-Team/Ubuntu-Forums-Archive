---
title: "Configuring Wacom cintiq 12wx"
date: 2012-05-23
forum: Hardware
---

### Post by AvixK7 on 2012-05-23
Hey everyone, I've never been able to get my wacom cintiq 12wx to work properly in Ubuntu. I figured I'd give it another shot.

Using Ubuntu 12.04. The cintiq model#: DTZ-1200W

I managed to get both screens running using the Nvidia X Server Settings, using twin view. Both screens are treated as a single screen, which isn't really what I want but it's the only way the cintiq screen is activating.

The pen is detected, but I can't calibrate it and the pen will cross to the other screen as if it is part of the cintiq.

Any advice would be appreciated :) 


Edit: I don't know why but The cintiq screen remains off. I can't get the screen to turn on.

```
lsusb
```
Bus 004 Device 004: ID 056a:00c6 Wacom Co., Ltd Cintiq 12WX

---

### Post by Favux on 2012-05-23
Hi AvixK7,

Check in the nVidia control panel and see if the Cintiq screen is disabled.  Apparently this version of it doesn't enable the Cintiq automatically like the older ones do.  If so enable it.

If that works then to get your pen confined to one screen despite the TwinView settings use the xsetwacom MapToOutput parameter:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)  It now supports TwinView/NVidia.  From the HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

Or maybe the "Map to Monitor" setting on the new Wacom Graphics Tablet applet in System Settings will handle that now.  Worth checking out.

---

### Post by AvixK7 on 2012-05-24
Hi Favux, Thanks for the tips! Twinview appears to be working.

I'll look over those links and get back to you. Thanks again!

---

### Post by AvixK7 on 2012-05-24
I've made some progress using the "xinput set-prop" command. The cursor is confined to the cintiq but I think my calculations for the transformation matrix is off, the cursor drifts away from the pen tip.

```
xinput set-prop "Wacom Cintiq 12WX stylus" --type=float "Coordinate Transformation Matrix" 0.432432432 0 0.567567568 0 1 0 0 0 1
```

Main screen is to the left (1680x1050), cintiq is to the right (1280x800)

Thanks again!

---

### Post by Favux on 2012-05-24
Sure.

I get:
```
xinput set-prop "Wacom Cintiq 12WX stylus" --type=float "Coordinate Transformation Matrix" 0.43243243 0 0.56756756 0 0.76190476 0 0 0 1
```

---

### Post by AvixK7 on 2012-05-24
That helped a lot, thank you :)

---

