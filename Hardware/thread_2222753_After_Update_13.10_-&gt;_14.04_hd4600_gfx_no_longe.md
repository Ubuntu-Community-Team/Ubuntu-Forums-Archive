---
title: "After Update 13.10 -&gt; 14.04 hd4600 gfx no longer working"
date: 2014-05-08
forum: Hardware
---

### Post by schmadde2 on 2014-05-08
Yesterday I upgraded my machine from 13.10 to 14.04. After that the Graphics Card is no longer working properly. The Resolution can only be set to a maximum of 1920x1200, while the native resolution of the monitor is 2560x1440. 

This is a HD4600 integrated into a Core i5 4570 (Haswell) CPU, the monitor is connected to the dual link dvi Port of the mainboard (DH87RL).

How can I resolve this problem?

---

### Post by sam-vilain on 2014-05-08
One workaround is to boot into the 13.10 kernel (Linux 3.11.0) at the grub screen (reboot & press escape before the splash screen)

---

### Post by schmadde2 on 2014-05-09
Thanks. This did the trick. Luckily the old kernel was still there so I only needed to configure grub accordingly.

---

