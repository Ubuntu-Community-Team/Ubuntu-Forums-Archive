---
title: "Wake-up from suspend to RAM results in black screen and static text mode cursor"
date: 2014-12-13
forum: Hardware
---

### Post by kaweka on 2014-12-13
Ubuntu 14.04 LTS on Pentium 4 APIC ACPI.
Going to suspend to disk works fine.
Dedicated graphic card ATI 9600.
However if to wake up the comp the black screen with text mode curser all the comp provides.
What could be possible reason?

---

### Post by papibe on 2014-12-13
Hi kaweka.

It may work forcing the system to going back to the graphic environment by pressing:
```
Ctrl+Alt+F7
```
Let us know if that makes a difference.
Regards.

---

### Post by kaweka on 2014-12-15
Hi, it turns out it is not only the graphics what has troubles. Also network is not working after resume. So sudo restart network-manager is necessary to get it working again. It seems a long search for root reason is going to be.

---

