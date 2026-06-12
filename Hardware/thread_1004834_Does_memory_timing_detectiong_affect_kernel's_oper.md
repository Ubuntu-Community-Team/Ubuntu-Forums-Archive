---
title: "Does memory timing detectiong affect kernel's operation?"
date: 2008-12-07
forum: Hardware
---

### Post by FIONEX on 2008-12-07
Hi,

My dual channel memory runs at 1066Mhz 5-5-5-15 (manually set in BIOS).  Mem test detects that it's 1066 at CAS 5, which is good.  However, when I boot and type "sudo lshw -c memory", I see that the kernel detects that the memory is running at 800 MHz.  Does this have any effect on how the kernel operates.  I'm just wondering if this would somehow limit the rate of data transfer to ram by the kernel.  Or is the transfer rate controlled only by the BIOS and the kernel just feeds it as much data as possible?

---

