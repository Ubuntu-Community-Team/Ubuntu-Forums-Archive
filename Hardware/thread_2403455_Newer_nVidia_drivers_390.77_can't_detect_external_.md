---
title: "Newer nVidia drivers 390.77 can't detect external display on Lenovo ThinkPad"
date: 2018-10-11
forum: Hardware
---

### Post by the-spyke on 2018-10-11
After recent update of nVidia drivers to 390.77 on Ubuntu 18.04 my external display stopped working. Is there some way to fix it (check X config/etc.) or at least to rollback to previous minor version of drivers (was 390.66 or something similar)? xrandr shows only internal screen.

Lenovo ThinkPad P50, nVidia Quadro M1000M
Ubuntu 18.04 (4.15.0-36-generic), nvidia 390.77

---

### Post by Autodave on 2018-10-11
If you go into Settings -> Additional Drivers you should be able to choose from several drivers.

---

### Post by the-spyke on 2018-10-11
I see only two: nvidia 390.77 tested and nouveau. If I try to apt install nvidia-384 or 375 it still installs 390.

---

### Post by Autodave on 2018-10-11
I apologize for giving you bad info: they used to always be listed there. Evidently, as I just found out for myself, they are no longer listed.  Maybe someone else will be able to help out here.

---

### Post by the-spyke on 2018-10-12
No problem. I Nvidia's bug report I see:
> ERROR: Kernel configuration is invalid."
include/generated/autoconf.h or include/config/auto.conf are missing."
Run 'make oldconfig && make prepare' on kernel src to fix it."
Is it safe to run those commands? Where I should run them? Thanks

---

### Post by the-spyke on 2018-10-15
Disabling NVIDIA KMS (enabled by default in 390.77) resolves the issue:
[COLOR=#333333][FONT=DINWebPro]Edit /lib/modprobe.d/nvidia-kms.conf file and set modeset to 0:[/FONT][/COLOR]
[COLOR=#333333][FONT=DINWebPro]options nvidia-drm modeset=0
[/FONT][/COLOR]
Save, update initramfs and reboot:
[COLOR=#333333][FONT=DINWebPro]sudo update-initramfs -u
reboot[/FONT][/COLOR]

---

