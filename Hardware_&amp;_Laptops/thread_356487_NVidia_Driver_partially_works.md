---
title: "NVidia Driver partially works"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by silas_irl on 2007-02-08
Yesterday I tried installing the NVidia driver, so since I'm lacking a decent internet connection I managed to download it NVIDIA-Linux-x86-1.0-9746-pkg1.run

The laptop I'm using is a HP Pavilion DV2175ea, with NVidia GO 7200 card.

It's the most recent version 1.0-9746

Anyway I shutdown X and logged in and installed the driver
  ```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

So it spits out that it doesn't have the modules for the kernel so it builds them and it goes fine and installs everything.

A simple 'startx' has me up and running in X.

Anyways when I reboot the machine, it complains that the NVidia driver is mismatched.  The X module has the version 1.0-9746 while the kernel module is version 1.0-7184 (which strangly is the version of NVidia's legacy driver). 

Also if I reinstall the driver again it'll let me start X, just not when booting up.

Anyone got any ideas how to fix it?

---

