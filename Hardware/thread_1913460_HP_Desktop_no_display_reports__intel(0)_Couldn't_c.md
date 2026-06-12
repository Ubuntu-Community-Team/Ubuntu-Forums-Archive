---
title: "HP Desktop no display reports  intel(0): Couldn't create pixmap for fbcon"
date: 2012-01-22
forum: Hardware
---

### Post by dlritchey on 2012-01-22
Yesterday my HP p7-1187c desktop (Intel i5 4-core, 8 GB RAM, intel display driver, Kubuntu 11.10) booted normally after installing a set of updates, but then went to a black screen.  Logging into the text-only display, found the following messages in Xorg.0.log:

[   346.011] (II) Open ACPI successful (/var/run/acpid.socket)
[   346.011] (EE) intel(0): Couldn't create pixmap for fbcon

Also found this messages in kern.log:

Jan 22 12:00:14 cdrcsi11 kernel: [  345.984804] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jan 22 12:00:23 cdrcsi11 kernel: [  354.577548] [drm:pch_irq_handler] *ERROR* PCH poison interrupt

Suggestions on how to fix this issue?

---

