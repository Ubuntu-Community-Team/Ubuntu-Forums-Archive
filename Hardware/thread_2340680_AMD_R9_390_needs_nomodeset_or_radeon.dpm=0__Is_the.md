---
title: "AMD R9 390 needs nomodeset or radeon.dpm=0  Is there anyway to get this card working?"
date: 2016-10-20
forum: Hardware
---

### Post by coldfuzin on 2016-10-20
I started out with a crash on GDM launch, but now am able to sort of use my install, albiet with awful video performance using radeon.dpm=0 in grub.  I tried the 4.8.2 kernel and it works wonderfully, but I lose HDMI audio (which I very much need.)
AMDGPU-PRO just causes a black screen with an unresponsive system. 
I also added ```
echo 'high' > '/sys/class/drm/card0/device/power_dpm_force_performance_level'
echo 'performance' > '/sys/class/drm/card0/device/power_dpm_state'
``` to rc.local and that at least gets me usable video acceleration, but the heat and power consumption when idling is nuts.

I've done heaps of googling, but I think I must be missing something.  Or is my only recourse buying a NVIDIA card? There was talk of no real useful support until 2018ish when DAL gets fixed or something?

---

### Post by mastablasta on 2016-10-21
go with new kernel and troubleshoot the HDMI audio losss.

AMDGPU-pro should support this card.

---

### Post by QIII on 2016-10-21
AMDGPU and -Pro *might* support this card if support for GCN 1.1 has arrived.  The R9 390 is GCN 1.1 hardware.  AMDGPU's initial support was for GCN 1.2 and later.

The R9 380 and 380X are GCN 1.2.  Inexplicably, the R9 390 series are not.  Thus, my R9 380X runs AMDGPU-Pro.

The Radeon driver would be installed by default with Ubuntu 16.04 and later with the R9 390.

---

### Post by coldfuzin on 2016-10-21
The lack of audio seems to due to no DAL support for bad code reasons.  There's lots of complaining and attempts at adding it manually with no luck, unless I missed someone getting it sorted?

---

