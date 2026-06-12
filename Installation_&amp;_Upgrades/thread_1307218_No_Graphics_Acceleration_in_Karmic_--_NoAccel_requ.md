---
title: "No Graphics Acceleration in Karmic -- NoAccel required"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by collix on 2009-10-30
Hi,

just upgraded to Karmic. Awesome, except for one small but annoying issue:
After upgrading, I couldn't log in. Entering my password in kdm resulted in crashing and restarting of the X server (and me entering my password again, etc.)
Everytime, the agpgart_amd64 module reported 
```

agpgart_amd64 0000:00:00.0: AGP 3.0 bridge
agpgart_amd64 0000:00:00.0: putting AGP V3 device into 8x mode

```
... after which dmesg revealed complaints like "mtrr: no MTRR for ... found".

Then, I remembered the NoAccel and ModeDebug options for xorg.conf, and lo and behold, X works when both are set to true. But graphics are **really** slow now.

I'm on an old BenQ Joybook (R22E) with a VIA chipset, using the openchrome driver (*01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)*)

Any ideas how to get rid of the NoAccel without losing X?

---

### Post by EdRoxter on 2010-01-10
Yep!

Instead of
```
Option "NoAccel" "true"
```
(you can delete that line)

look for
```
Section "ServerFlags"
[..]
EndSection
```

and add the line
```
Option "AIGLX" "off"
```
within.

This will obviously disable 3D acceleration but 2D acceleration will still be supported which makes the whole 2D graphics a lot faster. And since 3D acceleration of the UniChrome is quite bad anyway, you might not need it at all.

---

