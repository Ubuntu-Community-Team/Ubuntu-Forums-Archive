---
title: "ibm thinkpad 240x speed problem."
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by isw on 2006-06-24
Hello,

When running on AC my thinkpad 240x is reporting 497mhz at /proc/cpuinfo

but on battery it's only 147mhz.

Yes it preserves battery, but I need all the speed I can get. How do I disable the switch to less cpupower?

I run latest default updates, no acpi support in kernel by default. It doesn't wake up after going into hibernate or suspend, only thing that helps is to hardreset/reboot manually.

Any ideas?

thanks,

-- isw

---

### Post by isw on 2006-06-25
Well I solved the problem by disable the powersave feature to CPU in BIOS when running on battery, it now runs at 500 mhz at all time. :D

---

