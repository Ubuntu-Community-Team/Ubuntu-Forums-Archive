---
title: "HP NC8000: cpufreqd consumes CPU + ACPI fans"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by pilophae on 2007-12-04
Hi!

I'm running Ubuntu Gutsy Gibbon on a HP NC8000 notebook.
cpufreqd consumes a lot more CPU time than necessary, especially when load is low: up to 40%. It is the same with the vanilla config as with my own, and the poll_interval option does not seem to matter.

Also, the computer seems to have buggy ACPI temperature readings, since it will sporadically shut off at ~60°C, while the critical trip point is at 127°C. This may be related to the inability to manually control the fans, and what seems to be ACPI's inability to control the fans automatically. The fan problem doesn't seem to be a big deal, since 60°C is an acceptable temperature, but the sporadic heat-spikes are annoying and lowering the temperature seems to lessen their frequency.

Unfortunately, I haven't found any references to other NC8000:s with these problems or any blacklist entries in the kernel, so I'm a bit stumped.

Thankful for any help!

---

