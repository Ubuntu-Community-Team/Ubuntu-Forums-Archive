---
title: "Vaio VPCEB24FX Touchpad"
date: 2010-09-16
forum: Hardware
---

### Post by mykrob on 2010-09-16
Trying out Ubuntu Maverick Beta on my new Sony Vaio VPCEB24FX laptop. Everything worked out fine with the live cd, but upon installation, the touchpad doesnt work.

Ideas?

thanks,
-myk

---

### Post by zecapistolas on 2010-09-17
1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot

:KS

---

### Post by mykrob on 2010-09-19
turns out it was a regression in the kernel. Installing without running updates works fine, but the kernel update breaks the touchpad. I filed a bug report, and it has been resolved.

---

