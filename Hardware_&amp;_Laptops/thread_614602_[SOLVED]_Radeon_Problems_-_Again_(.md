---
title: "[SOLVED] Radeon Problems - Again :("
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by zoulman on 2007-11-16
Hey everyone,

I'm having problems getting direct rendering to work in ubuntu. The thing is, that I have had it working after installing the beta of 7.10 (sometimes) but ever since the final came out it hasn't functioned.

I have included my dmesg and lspci as attachments.

As you can see in dmesg i get some errors:

[   43.461046] [drm] Initialized drm 1.1.0 20060810
[   43.476033] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.476609] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   45.563301] [drm:radeon_cp_init] *ERROR* radeon_cp_init called without lock held
[   45.563348] [drm:drm_unlock] *ERROR* Process 5189 using kernel context 0

these seem to indicate that there is something wrong with my DRI and AGP not being initialized correctly, or am I wrong.

I have tried messing a bit around in my BIOS setting different AGP Aperature Sizes but without result.

Please help me out.

---

### Post by zoulman on 2007-11-16
bump

---

### Post by zoulman on 2007-11-19
bump

---

