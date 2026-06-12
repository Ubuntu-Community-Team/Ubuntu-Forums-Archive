---
title: "How do I enable High-res framebuffer with a EFI install using NVidia Prop. drivers?"
date: 2020-04-13
forum: Hardware
---

### Post by johnlbergqvist on 2020-04-13
Hi, i'm trying to enable a higher-resolution framebuffer on my system (which uses EFI & GRUB2) using the Nvidia proprietory drivers (nvidia-driver-440). How do i do this?

The guides i've found online are quite old now and no longer work (specifically `vbeinfo` is no longer there and `hwinfo --framebuffer` gives me nothing).

---

### Post by CatKiller on 2020-04-13
I've got ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
``` and ```
GRUB_GFXMODE=2560x1600x32,auto
GRUB_GFXPAYLOAD_LINUX=2560x1600x32
``` in my Grub config, and it works fine.

---

