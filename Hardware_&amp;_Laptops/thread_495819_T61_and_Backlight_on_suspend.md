---
title: "T61 and Backlight on suspend"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by ciphermonk on 2007-07-08
Something weird I haven't been able to figure out as yet, is why the backlight won't come back on when resuming from suspend. This is on a T61. Are any of you having this problem? If so, have you figured out how to fix it as yet?

---

### Post by meanimal on 2007-07-08
Pass acpi_sleep=s3_bios as a boot option to your kernel.  I put this into Grub's menu.lst and every suspend has succeeded since!  :)

---

### Post by ciphermonk on 2007-07-08
I did that and the backlight won't turn on... I ended up coming up with another fix that seems to be working pretty well.

[http://forums.fedoraforum.org/showthread.php?p=825257#post825257](http://forums.fedoraforum.org/showthread.php?p=825257#post825257)

---

