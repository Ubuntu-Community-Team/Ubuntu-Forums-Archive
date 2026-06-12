---
title: "Cannot enable frame buffer / LVDS"
date: 2012-04-19
forum: Hardware
---

### Post by Pille456 on 2012-04-19
Hi!

I'm running Xubuntu (XFCE 4.8, Kernel 3.0.0-17-generic) on a Samsung 900x3A and have less battery lifetime, than I should / could have.
Powertop tells me, that the laptop uses around 9 Watt in idle-mode and with no low backlight.
Using the laptop normal, it uses around 11 Watt, which leads to around 3 hours battery lifetime.
As far as I've read I can get around 7 Watt in idle-mode and 9 Watt while working.

I already set "i915.i915_enable_rc6=1" which works without any problems.
I tried to set "i915.i915_enable_fbc=1" and "i915.lvds_downclock=1", which lead to the following problem:
With one of these options enabled, I only have a maximum screen resolution of 1024x768 and compiz isnt working at all. Strange is this output:```

sudo hwinfo --framebuffer
[sudo] password for pille: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.ku_DuSHewh1
  Hardware Class: framebuffer
  Model: "Intel(R)Sandybridge Mobile Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Sandybridge Mobile Graphics Controller"
  SubVendor: "Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xb0000000-0xb3feffff (rw)
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```I'm currently running my laptop with its maximum resolution of 1366x768 which is not listed there.

Has anyone an idea what happens here and how I could solve it?

Thanks!

Pille

---

