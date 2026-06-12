---
title: "Single core detected (core i7 processor)"
date: 2010-02-17
forum: Hardware
---

### Post by atiketemola on 2010-02-17
Hi,

I've installed Ubuntu 9.10 amd64 on my laptop (core i7 820 processor with 4 Gb of RAM) using the noapic and nolapic kernel boot options. The problem is that 1) it only detects one of the eight cores and 2) it's totally unstable. I've tried to change the kernel boot options unsuccesfully (noapic + acpi=noirq, noapic + acpi=off, noapictimer, no_timer_check, etc.)

If I install Ubuntu 9.10 i386 it detects the 8 cores but only 3'1 Gb of RAM and, when I update, it installs the PAE kernel and the same problems of the amd64 version reappear.

I've also tried to install from the alternate CD with the same results. Finally, installing Debian 5.04 amd64 it detects OK the processor and the memory (but not the ethernet card which is a JMC250!). NOTE: According Memtest, RAM is OK.

Any ideas? Help would be highly appreciated...

Thanks in advance.

---

### Post by msrinath80 on 2010-02-17
Support for the new corei* series of CPUs is more mature only in the *latest* kernels. Try using Lucid Lynx. Also, there are only 4 cores, but 8 threads in the 820QM.

---

### Post by atiketemola on 2010-02-18
It works! I've installed Lucid alpha 2 and it detects the 8 cpu threads & the 4gb RAM (msrinath80, you're right there are just 4 cores).

Now my problem is that Lucid doesn't detect neither the ethernet card (Jmicron JMC250) nor the wireless card (Realtek RTL8187SE) so I will have to download the packages needed to build the drivers in another laptop.

---

