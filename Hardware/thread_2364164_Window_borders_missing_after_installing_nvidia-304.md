---
title: "Window borders missing after installing nvidia-304 in Kubuntu 12.04"
date: 2017-06-19
forum: Hardware
---

### Post by firehammer047 on 2017-06-19
Full, summarized story:


- Have a Kubuntu 12.04 system running on AMD Phenom, so a bit older hardware.

- Bought GTX 1050 Ti for GPGPU, and installed nvidia-375 via apt-get (unofficial PPA).

- KDE (plasma-desktop) looked great after installing drivers.

- Remote logged-in and installed nvidia-cuda-toolkit (which installed nvidia-304) and corrupted my KDE causing borderless windows and unusable desktop.

- Uninstalled/reinstalled nvidia-304, 375, and 378, current, current-updates, and several combinations. No success.

The 304 driver doesn't support the 1050 card, but it's what is installed for Ubuntu 12.04.


FINAL FIX: Uninstalled (purge) all nvidia packages. Uninstalled plasma-desktop. Reinstalled plasma-desktop (noticed k-window-manager was being installed again) Reinstalled nvidia-375


Desktop working.

---

### Post by howefield on 2017-06-20
> **firehammer047 said:**
> ....Desktop working.

But sadly long since went End of Life and therefore unsupported.

---

