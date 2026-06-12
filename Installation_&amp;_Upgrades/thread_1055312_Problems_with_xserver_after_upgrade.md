---
title: "Problems with xserver after upgrade"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by proteo on 2009-01-30
After upgrading to kernel 2.6.27-11 I restarted my laptop and only got a black screen with a blinking cursor, tried starting on recovery mode and running xfix option and only got to the CLI login prompt.
I was using the fglrx ATI driverfrom the repositories before the update, and it looks like it's trying to use the radeon driver now. But I can still load gnome with the older kernel yet.

Any help please?

---

### Post by em4r1z on 2009-01-30
Stick with the older kernel or use the latest one without the ATI drivers. The new kernel caused a fatal kernel panic on my laptop and I was forced to reinstall (for the kernel panic affected all my available kernels.) If your hardware is working fine, you'll hardly need the new kernel.

---

### Post by proteo on 2009-01-30
Thanks, I hope they fix that problem, I'll use the older kernel meanwhile.

---

