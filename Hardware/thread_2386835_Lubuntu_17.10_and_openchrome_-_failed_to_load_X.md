---
title: "Lubuntu 17.10 and openchrome - failed to load X"
date: 2018-03-11
forum: Hardware
---

### Post by ozzie1 on 2018-03-11
I decided to grab an old Neoware Via C7/CN700 thin client and set it up to watch Plex videos and play emulators on my TV. I loaded Lubuntu 17.10, but the screen resolution was stuck at 640x480. I installed the xserver-xorg-video-openchrome driver, rebooted, and got nothing but a blank screen. Checking Xorg.1.log, I found this:

```
[  1169.048] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration[  1169.054] (--) PCI:*(0:1:0:0) 1106:3344:1106:3344 rev 1, Mem @ 0xf4000000/67108864, 0xfb000000/16777216, BIOS @ 0x????????/131072
[  1169.054] (II) LoadModule: "glx"
[  1169.055] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1169.117] (II) Module glx: vendor="X.Org Foundation"
[  1169.128]     compiled for 1.19.5, module version = 1.0.0
[  1169.128]     ABI class: X.Org Server Extension, version 10.0
[  1169.128] (==) Matched openchrome as autoconfigured driver 0
[  1169.128] (==) Matched modesetting as autoconfigured driver 1
[  1169.128] (==) Matched fbdev as autoconfigured driver 2
[  1169.128] (==) Matched vesa as autoconfigured driver 3
[  1169.128] (==) Assigned the driver to the xf86ConfigLayout
[  1169.128] (II) LoadModule: "openchrome"
[  1169.130] (WW) Warning, couldn't open module openchrome
[  1169.130] (II) UnloadModule: "openchrome"
[  1169.130] (II) Unloading openchrome
[  1169.130] (EE) Failed to load module "openchrome" (module does not exist, 0)
```

I ran X -configure and installed the xorg.conf, but same result, the openchrome driver doesn't exist. The [Openchrome install instructions]("https://www.freedesktop.org/wiki/Openchrome/Installation/") reference to an "xf86-video-openchrome", but I think it's the same driver with a different name. I have not tried compiling from scratch yet, mostly because the 4GB DOM is nearly full. I realize that this is damn near ancient hardware at this point, but anyone got any tips on how to get it working?

edit: I verified "[COLOR=#2E1A05]/usr/lib/xorg/modules/drivers/openchrome_drv.so" is present, but I don't know how to e.g. force it to load.[/COLOR]

---

