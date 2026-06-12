---
title: "boot problem"
date: 2010-08-11
forum: Hardware
---

### Post by irakla7777777 on 2010-08-11
hi all
I have compiled a new kernel 2.6.35 and I can not boot because same error :
kernel panic - Unable to mount root fs on unknown-block(0,0).
i have motherboard ga-p55a-ud3r and controlleris sata .now i use channel in ACHI mode. when i change it in ide mode it boots but in low graphic mode. then i have compiled modules again with support ACHI_SATA mdoe in xconfig of kernel. but same error occur.
can anyone help me


thanks

---

### Post by Fafler on 2010-08-11
Rebuild the kernel with AHCI support or build a initrd with the AHCI module. But why aren't you just using the stock Ubuntu kernel?

---

