---
title: "Setting Console screen size"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by MichaelBaum on 2006-11-29
This *may* be an FAQ, but so far all of the threads I've read on problems with laptop screen resolution seem concerned with the X Window server. On my old Toshiba Satellite, the generic Ubuntu/Kubuntu set-up for Edgy Eft worked just ducky for setting up the X server. However when I switch to console mode, the system ignores everything the x server knows about resolution and just uses the center third of the screen. I can't seem to find where this is controlled. Is it an option in the bootloader?

maab

---

### Post by ingo on 2006-12-01
not sure how you would use it, but could just try to append it to the GRUB line

> fb1024x768

---

