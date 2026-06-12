---
title: "kernel 2.6.12-10-686 upgrade fail to boot"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by linuxfj on 2005-11-29
Via the update manager, I installed kernel 2.6.12-10-686 on an Acer Travelmate 4602WLMi.

Now it hangs at the following point:
* Loading ACPI modules...     y...                         [OK]

How do I find out what the problem is? Is it once again the dreaded ACPI issue or something just after it? What is this "y..."?

Kernel 2.6.12-9-686 does not give this problem.

---

### Post by linuxfj on 2005-11-29
Just to confirm that ACPI is the problem!

---

### Post by teaker1s on 2005-11-29
hit escape at grub boot your previous kernel and use synaptic to check that the latest kernel has latest restricted modules loaded-this was left out on both 386i and k7 kernel  updates,so I would guess it's a good place to start:KS

---

### Post by linuxfj on 2005-12-01
Upgraded the bios, no problem with the kernel installation, but still no ACPI!

---

