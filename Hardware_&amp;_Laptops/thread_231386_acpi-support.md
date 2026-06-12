---
title: "acpi-support"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by acojlo on 2006-08-07
Which part of Ubuntu is responsible for failed resume from S3? Is it acpi-support with the scripts or kernel?

---

### Post by isharra on 2006-08-07
Short answer, maybe both. You give no specifics. Improperly setting up acpi-support can cause it. Bad drivers (usually but not always supplied by the kernel) will definately cause it.

I ended up compiling a custom kernel (linux-2.6.17.8 straight from kernel.org) and making minor changes to the acpi-support settings to get suspend and hibernate working for me. The version of cs46xx alsa driver in that kernel will allow suspend and resume instead of halting or crashing, though you still need to remove it and reload it to keep sound working (argh).

---

### Post by deewoo on 2006-08-11
isharra, what exact changes did you make to acpi when you recompiled the kernel?  Could you post your .config file?  Thanks

Dennis

---

