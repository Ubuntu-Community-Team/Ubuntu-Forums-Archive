---
title: "Nvidia screen resolution(Solved)"
date: 2013-04-28
forum: Hardware
---

### Post by eddier on 2013-04-28
I tried ubuntu studio13.04 beta a few weeks ago and ran into screen resolution problems,I could not get better than 1024x768 on a 1680x1050 display.

Graphics card is nvidia 7600GS and the driver is 304. 

I decided to wait for the final to be released hoping the problem would be solved. Sadly it isnt.

Nvidia settings claims that the drivers are not in use. They are, however, installed.

Previous 12.10 studio gave no problems whatsoever.

Can someone guide me through troubleshooting this problem-my Terminal abilities are not that advanced!

thanks up front
eddie


P.S. I have the following in var/log/xorg.0.log

```
[    21.996] (II) LoadModule: "glx"
[    22.074] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    23.597] (II) Module glx: vendor="NVIDIA Corporation"
[    23.597] 	compiled for 4.0.2, module version = 1.0.0
[    23.597] 	Module class: X.Org Server Extension
[    23.597] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    23.597] Loading extension GLX
[    23.597] (II) LoadModule: "nvidia"
[    23.597] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.692] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.692] 	compiled for 4.0.2, module version = 1.0.0
[    23.692] 	Module class: X.Org Video Driver
[    23.733] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    23.733] (EE) NVIDIA:     system's kernel log for additional error messages.
[    23.733] (II) UnloadModule: "nvidia"
[    23.733] (II) Unloading nvidia
[    23.733] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    23.733] (==) Matched nvidia as autoconfigured driver 0
[    23.733] (==) Matched nouveau as autoconfigured driver 1
[    23.733] (==) Matched vesa as autoconfigured driver 2
[    23.733] (==) Matched modesetting as autoconfigured driver 3
[    23.733] (==) Matched fbdev as autoconfigured driver 4
[    23.733] (==) Assigned the driver to the xf86ConfigLayout
[    23.733] (II) LoadModule: "nvidia"
[    23.733] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.734] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.734] 	compiled for 4.0.2, module version = 1.0.0
[    23.734] 	Module class: X.Org Video Driver
[    23.737] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    23.737] (EE) NVIDIA:     system's kernel log for additional error messages.
[    23.737] (II) UnloadModule: "nvidia"
[    23.737] (II) Unloading nvidia
[    23.738] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    23.738] (II) LoadModule: "nouveau"
[    23.751] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.784] (II) Module nouveau: vendor="X.Org Foundation"
[    23.784] 	compiled for 1.13.3, module version = 1.0.7
[    23.784] 	Module class: X.Org Video Driver
[    23.784] 	ABI class: X.Org Video Driver, version 13.1
[    23.784] (II) LoadModule: "vesa"
[    23.784] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.790] (II) Module vesa: vendor="X.Org Foundation"
[    23.790] 	compiled for 1.12.99.902, module version = 2.3.2
[    23.790] 	Module class: X.Org Video Driver
[    23.790] 	ABI class: X.Org Video Driver, version 13.0
[    23.790] (II) LoadModule: "modesetting"
[    23.790] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.806] (II) Module modesetting: vendor="X.Org Foundation"
[    23.806] 	compiled for 1.13.3, module version = 0.7.0
[    23.806] 	Module class: X.Org Video Driver
[    23.806] 	ABI class: X.Org Video Driver, version 13.1
[    23.806] (II) LoadModule: "fbdev"
[    23.806] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.821] (II) Module fbdev: vendor="X.Org Foundation"
[    23.821] 	compiled for 1.12.99.902, module version = 0.4.3
[    23.821] 	Module class: X.Org Video Driver
[    23.821] 	ABI class: X.Org Video Driver, version 13.0
[    23.821] (II) NOUVEAU driver Date:   Wed Mar 27 09:50:03 2013 +0100
[    23.821] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.821] 	RIVA TNT        (NV04)
[    23.821] 	RIVA TNT2       (NV05)
[    23.821] 	GeForce 256     (NV10)
[    23.821] 	GeForce 2       (NV11, NV15)
[    23.821] 	GeForce 4MX     (NV17, NV18)
[    23.821] 	GeForce 3       (NV20)
[    23.821] 	GeForce 4Ti     (NV25, NV28)
[    23.821] 	GeForce FX      (NV3x)
[    23.821] 	GeForce 6       (NV4x)
[    23.821] 	GeForce 7       (G7x)
[    23.821] 	GeForce 8       (G8x)
[    23.821] 	GeForce GTX 200 (NVA0)
[    23.821] 	GeForce GTX 400 (NVC0)
[    23.821] (II) VESA: driver for VESA chipsets: vesa
[    23.821] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.821] (II) FBDEV: driver for framebuffer: fbdev
[    23.821] (++) using VT number 7
```

---

### Post by eddier on 2013-04-28
Well,I jumped the gun there! Sorted.

```
Sudo apt-get purge nvidia-304
```

```
sudo apt-get install nvidia-173
```

Whats going on there then? How come the newer drivers wont work?

eddie

---

