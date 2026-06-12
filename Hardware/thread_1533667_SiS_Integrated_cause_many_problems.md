---
title: "SiS Integrated cause many problems"
date: 2010-07-18
forum: Hardware
---

### Post by orduek on 2010-07-18
Is there any solution in near future?
I just bought an LG laptop with SIS chipset and SIS graphic card (671/771) and SIS 191 ethernet adaptor.
Its a NIGHTMARE!
I'm working for more than two days trying to put everything together.
I managed to solve the graphic card problem but still find it extremely hard to solve the ethernet adaptor problem.
Will there be a solution?

---

### Post by Roehrich on 2010-07-22
What's the problem with that adapter?

I'm not using Ubuntu but Mandriva on a SiS-based notebook, and the SiS 191 Gigabit Ethernet Adapter works fine
(btw: Mandriva is still best Distribution for SiS based hardware).
The driver for that adapter comes as kernel module sis190 since years, so there should basically be no extra effort necessary to get it running...?

My ethernet adapter:
```
# lspci -nn
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
```

---

### Post by orduek on 2010-07-26
You are right.
The problem is with the realtek rtl8192se wireless adapter. When disabling it - everything works fine.
Thank you.

---

