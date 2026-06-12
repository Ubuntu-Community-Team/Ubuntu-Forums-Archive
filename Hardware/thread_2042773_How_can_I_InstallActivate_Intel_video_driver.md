---
title: "How can I Install/Activate Intel video driver?"
date: 2012-08-15
forum: Hardware
---

### Post by rrrobles on 2012-08-15
I'm running a Vostro 3460 with Ubuntu 11.10. I made a new fresh install and all the hardware works, except video that falls in VESA instead of Intel.
This notebook have a Nvidia Optimus technology with two video boards: one Intel® HD Graphics and the other is GeForce GT630M.
I managed to install Bumblebee with success, and through it I can get reasonable FPS, but the main video is running VESA instead of Intel.
I made some research but have no idea how to activate the Intel video driver.

lspci output:

```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0de9 (rev ff)

```

lshw -c video output:

```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

```

---

### Post by rrrobles on 2012-08-16
Solved. Removing an unnecessary 'nomodeset' option in /boot/grub/grub.cfg solved the problem.
The option was there because during first install it was necessary to get the video working.

---

