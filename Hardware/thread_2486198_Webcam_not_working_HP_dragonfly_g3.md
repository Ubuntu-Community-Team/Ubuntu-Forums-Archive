---
title: "Webcam not working HP dragonfly g3"
date: 2023-04-22
forum: Hardware
---

### Post by freddo23 on 2023-04-22
Hi,
I'm running Ubuntu 22.10 on HP Elite dragonfly G3 (2023), not so smoothly. The webcam is not working (at all), among other problems.

~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 06cb:0103 Synaptics, Inc. 
Bus 003 Device 002: ID 18a5:0302 Verbatim, Ltd Flash Drive
Bus 003 Device 004: ID 8087:0033 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lshw -c media : doesn't give anything

$ inxi -Gx
Graphics:
  Device-1: Intel Alder Lake-UP3 GT2 [Iris Xe Graphics]
    vendor: Hewlett-Packard driver: i915 v: kernel arch: Gen-12.2
    bus-ID: 00:02.0
  Display: x11 server: X.Org v: 1.21.1.4 with: Xwayland v: 22.1.3 driver:
    X: loaded: modesetting unloaded: fbdev,vesa gpu: i915
    resolution: 1920x1280~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 22.2.5
    direct render: Yes
And compatibility test here: [https://linux-hardware.org/?probe=2a5d9adcd4](https://linux-hardware.org/?probe=2a5d9adcd4)

---

