---
title: "VAIO doesn't power off after shutdown"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Cmdrfletcher on 2005-06-27
Hi,

I'm using a Sony VAIO VGN-A115M Laptop and Ubuntu 5.04.

Everything is working great and I'm very happy with Ubuntu. :)

Except one thing:

When I shutdown the Laptop it won't power off after the shutdown-process. I can hear the HD "clicking" (indicating that it is off) and  the screen is going off (black). But somehow the laptop is still running (fan spinnig and LEDs are on).

Any solutions?

---

### Post by luca_linux on 2005-06-27
Check if there's a module called sony*.ko or something like that and load it if it's not already loaded.
If the problem is still there, try to pass the kernel parameter "nolapic" at boot. This should work.
Then let me know.

---

### Post by Cmdrfletcher on 2005-06-28
How can I determine if a module is loaded?

---

### Post by luca_linux on 2005-06-28
```
lsmod
```
This command gives you a list of the loaded modules.

---

### Post by Cmdrfletcher on 2005-06-28
Result of

lsmod | grep 'sony'
sony_acpi               6280  0

---

### Post by luca_linux on 2005-06-28
Try passing "nolapic" kernel parameter at boot.

---

