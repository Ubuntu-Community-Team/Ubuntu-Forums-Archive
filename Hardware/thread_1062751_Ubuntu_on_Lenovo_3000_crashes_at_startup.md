---
title: "Ubuntu on Lenovo 3000 crashes at startup"
date: 2009-02-07
forum: Hardware
---

### Post by toaster9 on 2009-02-07
hi, i got a startup problem with ubuntu (8.10) on my lenovo 3000 N200; Everything goes fine until the orange bar appears, then after a few seconds the computer shuts down as if i'd pull the plug, before that, the fan turns on at full speed, after about 5 times of rebooting it starts up normally. What's wrong?

---

### Post by overdrank on 2009-02-07
> **toaster9 said:**
> hi, i got a startup problem with ubuntu (8.10) on my lenovo 3000 N200; Everything goes fine until the orange bar appears, then after a few seconds the computer shuts down as if i'd pull the plug, before that, the fan turns on at full speed, after about 5 times of rebooting it starts up normally. What's wrong?

Hi and welcome, You may try and boot into recovery mode, Which is usually the second choice from the grub. This way the splash is removed and you may see any errors if any.

---

### Post by toaster9 on 2009-02-09
well, I started in recovery mode but can't see any errors, it goes through these lists quite fast and shuts down but doesn't hang anywhere. Is it possible that it has something to do with the BIOS? It is not the latest version, but I can't update it since I removed Windows from my computer.

---

### Post by HyRax on 2009-02-09
> **toaster9 said:**
> well, I started in recovery mode but can't see any errors, it goes through these lists quite fast and shuts down but doesn't hang anywhere. Is it possible that it has something to do with the BIOS? It is not the latest version, but I can't update it since I removed Windows from my computer.

You shouldn't need Windows to update the BIOS - most manufacturers now allow for reading the BIOS file off a FAT32-formatted USB stick these days (like the EeePC). Just check your manual.

In the meantime, I'd suggest going into the BIOS, reset to factory defaults, save, reboot and try again. Failing that, go into the BIOS and disable anything ACPI-related and try again.

---

### Post by toaster9 on 2009-02-09
Wow, thanks a lot, it worked! I've reset BIOS to factory defaults and now everything is fine! Great!

---

