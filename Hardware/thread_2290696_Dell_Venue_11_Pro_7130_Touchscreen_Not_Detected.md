---
title: "Dell Venue 11 Pro 7130 Touchscreen Not Detected"
date: 2015-08-14
forum: Hardware
---

### Post by Jian-Long_Liu on 2015-08-14
I'm at a loss of where to start debugging. It's the same bug outlined [here]("https://bugzilla.kernel.org/show_bug.cgi?id=91281").
Basically, the touchscreen SYNA7500:00 06CB:3AF0 gets detected and works perfectly in Arch, but in Ubuntu (Vivid, tried various kernels from 3.16 to 3.18; 3.19+ needs to have the patch listed [here]("https://bugzilla.kernel.org/show_bug.cgi?id=94281") reverted for it to work on Arch, and I don't feel like compiling), it doesn't get detected.
dmesg doesn't show any problems, the touchscreen just doesn't appear. The device doesn't get listed under /sys/bus/i2c/devices and /sys/bus/acpi/devices.

Any ideas?

---

### Post by Jian-Long_Liu on 2015-08-17
Bump.

---

### Post by Jian-Long_Liu on 2015-08-19
Bump.

---

### Post by Jian-Long_Liu on 2015-08-24
Bump.

---

### Post by isnogood2 on 2015-11-05
This thread [http://ubuntuforums.org/showthread.php?t=2187204&page=15](http://ubuntuforums.org/showthread.php?t=2187204&page=15) and this Bugreport [https://bugzilla.kernel.org/show_bug.cgi?id=94281](https://bugzilla.kernel.org/show_bug.cgi?id=94281) should be of interest to you.
I can confirm, that the touchscreen works under kernel 3.18.6 9 out of 10 times, even in Ubuntu 15.10. I now have Fedora 23 installed on my Venue 11 pro (they already included automatic screen rotation).
I will try out the patch, provided in the bugreport, as soon as I got the time.

regards,
Isnogood

---

