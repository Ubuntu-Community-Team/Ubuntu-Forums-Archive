---
title: "[Resolved]ATI radeon GLX problem"
date: 2017-07-06
forum: Hardware
---

### Post by impeto on 2017-07-06
Hello,

I'm trying to configure an old gpu AMD card on ubuntu 16.04 and I need help.

This is the card:
```

*-display UNCLAIMED     
       description: VGA compatible controller
       product: Caicos PRO [Radeon HD 7450]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:fe620000-fe63ffff ioport:e000(size=256) memory:c0000-dffff

```

This is glxinfo:
```

LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: DRI3 is disabled, try running in DRI2 mode. xorg version is 0
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/swrast_dri.so
libGL: dlopen /usr/X11R6/lib64/modules/dri/swrast_dri.so failed (/usr/X11R6/lib64/modules/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib64/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib64/dri/swrast_dri.so
libGL: dlopen /usr/lib64/dri/swrast_dri.so failed (/usr/lib64/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/swrast_dri.so
libGL: dlopen /usr/X11R6/lib/modules/dri/swrast_dri.so failed (/usr/X11R6/lib/modules/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib32/modules/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib32/modules/dri/swrast_dri.so
libGL: dlopen /usr/X11R6/lib32/modules/dri/swrast_dri.so failed (/usr/X11R6/lib32/modules/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/dri/swrast_dri.so
libGL: dlopen /usr/lib32/dri/swrast_dri.so failed (/usr/lib32/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  6 (X_GLXIsDirect)
  Serial number of failed request:  46
  Current serial number in output stream:  45

```

This is strange because there is a swrast_dri.so in this folder /usr/lib/x86_64-linux-gnu/dri/

In my xorg log I only have this error:
```

II) [KMS] drm report modesetting isn't supported.
[  1904.022] (EE) open /dev/dri/card0: No such file or directory
[  1904.022] (WW) Falling back to old probe method for modesetting
[  1904.022] (EE) open /dev/dri/card0: No such file or directory

```

After googoling I still don't know how to solve this :( , please I need some help!

---

### Post by impeto on 2017-07-07
you can close 
after upgrading to ubuntu 16.10 i found ati dedicated driver installed

so amdgpu-pro-uninstall

dpkg-reconfigure xorg

and all working :D

---

### Post by slickymaster on 2017-07-07
Thread moved to **Hardware** for a better fit

---

