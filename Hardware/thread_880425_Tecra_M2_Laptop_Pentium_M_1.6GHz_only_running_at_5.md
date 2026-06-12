---
title: "Tecra M2 Laptop Pentium M 1.6GHz only running at 598 MHz"
date: 2008-08-05
forum: Hardware
---

### Post by supercompman on 2008-08-05
I have a Toshiba Tecra M2 laptop with a 1.6GHz Pentium M processor, 2GB RAM, and I'm using the Nvidia restricted drivers with Hardy. When trying to add the CPU Frequency Scaling monitor to the Gnome panel, it informs me that this system does not support CPU frequency scaling and reports that the system is only running at 598MHz. After investigating a bit more, I discovered that /sys/devices/system/cpu/cpu0/cpufreq does not exist, suggesting that Ubuntu really doesn't see that this system supports frequency scaling and when doing cat /proc/cpuinfo it does show the processor running at 598.541MHz regardless of the load I place on the system. I have attempted using all versions of Ubuntu clear back to 6.04 with exactly the same results. I have also verified that in fact the system is only running at 598MHz through a little benchmarking of this system compared to a 1.5GHz Via C7 system... the C7 beat this laptop in nearly every test, when I know that this Pentium M should be significantly faster. Has anyone seen this behavior before, and if so, is there anything I can do to correct it? Thanks in advance.

---

### Post by supercompman on 2008-08-05
I have now also tested with the Xorg Nvidia driver instead of the restricted driver and it has no affect on the CPU scaling at all. The problem still exists and I'm out of ideas.

---

