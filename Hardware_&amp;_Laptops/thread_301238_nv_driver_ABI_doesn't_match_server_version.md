---
title: "nv driver: ABI doesn't match server version"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by jabster on 2006-11-16
Hi.
 
I just upgraded from kubuntu dapper to edgy last night/this morning folling these directons: [http://kubuntu.org/announcements/6.10-release.php](http://kubuntu.org/announcements/6.10-release.php)
 
Upgrade seemed to go well...no errors...just some LC_ALL warnings during some program installations.
 
However, when I rebooted, X did not start. I get a no screens error found, with the errors noted below. This is with the "nv" driver. If I change the driver to "nvidia" X starts, but I only get 1024x768 resolution, whereas I get 1280x1024 with "nv" (side note: can someone explain that?).
 
Any ideas on what's going on here? I can understand "nvidia" not working...but "nv"?!?
 
My X log is below.
 
thanks,
john

====
```
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(EE) Failed to load module "nv" (module requirement mismatch, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(EE) No drivers available.

Fatal server error:
no screens found
```

---

### Post by Joe_CoT on 2006-11-16
Make sure you have the kubuntu-desktop package installed. the video driver packages all changed, and they aren't reflected if you don't have the metapackage.

---

### Post by jabster on 2006-11-18
> **Joe_CoT said:**
> Make sure you have the kubuntu-desktop package installed. the video driver packages all changed, and they aren't reflected if you don't have the metapackage.

Joe,

If you look at the upgrade link above, installing kubuntu-desktop is one of the steps, which I did.

However, you are correct in that the driver name did change. Actually found it on a german website (you know, the ones I typically skip on a google search because I can't read german) that had it almost right. "sudo apt-get server-xorg-video-nv" It's actually xserver. For some inane reason (to me anyways), it was changed from xserver-xorg-driver-nv.

For whatever reason, the nv driver did not get upgraded during the edgy upgrade. Did the apt-get install above, and now nv works fine.

thanks,
john


p.s. Any ideas why nv gives me a higher resolution than nvidia? 1280x1024 max vs 1024x768 max? Generic 17" CRT monitor.

---

