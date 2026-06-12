---
title: "Make ubuntu 16.04 installation dual boot as VMware guest"
date: 2016-05-30
forum: Hardware
---

### Post by Vasili_Pupkin on 2016-05-30
Is there any way how one can temporarily switch off NVIDIA driver? Its GLX extension in particular. I am trying to boot my machine as VMware guest and having these errors:

Xorg.0.log
```
...
[    49.993] (II) "glx" will be loaded by default.
[    49.993] (II) LoadModule: "glx"
[    49.993] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so 
[    49.998] (II) Module glx: vendor="NVIDIA Corporation"
[    49.998] (II) NVIDIA GLX Module  304.131  Sun Nov  8 22:03:20 PST 2015
[    49.998] (==) Matched vmware as autoconfigured driver 0
[    49.998] (==) Matched vmware as autoconfigured driver 1
[    49.998] (==) Matched modesetting as autoconfigured driver 2
[    49.998] (==) Matched fbdev as autoconfigured driver 3
[    49.998] (==) Matched vesa as autoconfigured driver 4
[    49.998] (==) Assigned the driver to the xf86ConfigLayout
[    49.998] (II) LoadModule: "vmware"
[    49.998] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[    50.005] (II) Module vmware: vendor="X.Org Foundation"
...
[    50.005] (II) LoadModule: "vesa"
[    50.005] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    50.005] (II) Module vesa: vendor="X.Org Foundation"
[    50.005]     compiled for 1.18.1, module version = 2.3.4
[    50.005]     Module class: X.Org Video Driver
[    50.005]     ABI class: X.Org Video Driver, version 20.0
[    50.005] (II) vmware: driver for VMware SVGA: vmware0405, vmware0710
...
[    50.008] (WW) vmware(0): Disabling 3D support.
[    50.008] (WW) vmware(0): Disabling Render Acceleration.
[    50.008] (WW) vmware(0): Disabling RandR12+ support.
[    50.008] (--) vmware(0): VMware SVGA regs at (0x1090, 0x1091)
[    50.008] (II) Loading sub module "vgahw"
[    50.008] (II) LoadModule: "vgahw"
[    50.008] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    50.008] (II) Module vgahw: vendor="X.Org Foundation"
...
[    50.106] (II) UnloadModule: "vesa"
[    50.106] (II) Unloading vesa
[    50.106] (--) Depth 24 pixmap format is 32 bpp
[    50.106] (II) vmware(0): Initialized VMWARE_CTRL extension version 0.2
[    50.106] (II) vmware(0): Initialized VMware Xinerama extension.
[    50.106] (II) vmware(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    50.172] (==) vmware(0): Backing store enabled
[    50.172] (==) vmware(0): Silken mouse enabled
[    50.173] (II) vmware(0): Initialized VMware Xv extension successfully.
[    50.173] (==) RandR enabled
[    50.175] (II) SELinux: Disabled on system
[    50.175] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found) 

```

.xsession-errors
```

Xlib:  extension "GLX" missing on display ":0".
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (1678) terminated with status 1
upstart: unity-settings-daemon main process (1666) killed by TERM signal 
...

```

---

