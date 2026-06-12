---
title: "ATI, dual monitor trouble, no signal to CRT"
date: 2008-06-21
forum: Hardware
---

### Post by burton247 on 2008-06-21
As the title shows i cant setup dual monitors. By default i thought plugging an external monitor into the laptop should just clone screen?
Even so, its not :(
and i wondered if anyone could help me, its a pretty old laptop

Output of lspci give

```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

I really would like to get an extended desktop sorted, but without it cloning im getting nowhere. If the monitor is attached during boot the signal is outputted through the external, soon as X starts, turns off and back to laptop screen.

Any ideas?

Thanks

---

### Post by kagashe on 2008-06-28
Dual monitor for this card works in Gutsy but not in Hardy due to [this bug]("http://bugs.freedesktop.org/show_bug.cgi?id=15708").

The bug has been removed in the latest git version of the driver and the updated driver should be in Ubuntu repositories any time now.

If you are in a hurry you could download the following .deb packages from Debian Sid repositories and install through dpkg:
xserver-xorg-video-ati_6.8.192-1_i386.deb
xserver-xorg-video-mach64_6.8.0-1_i386.deb
xserver-xorg-video-r128_6.8.0-1_i386
xserver-xorg-video-radeon_6.8.192-1_i386

Please note that the first driver (ati) has a dependency on others, so install them first and then ati.

kagashe

---

