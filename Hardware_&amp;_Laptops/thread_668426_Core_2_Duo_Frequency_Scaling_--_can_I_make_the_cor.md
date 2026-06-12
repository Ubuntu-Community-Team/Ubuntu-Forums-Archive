---
title: "Core 2 Duo Frequency Scaling -- can I make the cores scale independtly of each other?"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2008-01-15
I have an Intel Core 2 Duo (Dual core) @ 2.0 GHz, and right now, when I'm using my laptop, if one core requires a frequency change, they both do. Is this something I can configure (have either C PU scale up as the need arises), because here's my issue:

If one process is putting a heavy load on the CPU, then the ondemand govenor will scale that CPU up. But if it's only one process, there (AFAIK) is no way to split that process across cores, so why scale up the second core?

Oh yeah, and I'm on gutsy as well.

---

### Post by enigma_0Z on 2008-01-17
*bump*

No one? Can't someone tell me if the Core 2 Duo's can scale the cores independently? On my system /sys/devices/system/cpu/cpu1 is a symlink to cpu0... is this wrong??

Thanks.

---

