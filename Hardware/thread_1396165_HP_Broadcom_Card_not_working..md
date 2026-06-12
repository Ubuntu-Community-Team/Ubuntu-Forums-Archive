---
title: "HP Broadcom Card not working."
date: 2010-02-01
forum: Hardware
---

### Post by astrotrain12 on 2010-02-01
[SIZE=2]I just installed 9.10 using Wubi onto a separate partition of my C drive on my HP Pavilion DV9700 laptop. I have a AMD TurionX2 64 bit processor. The wireless works when in Windows but not in Ubuntu. I tried going to SYSTEM>Admin>Hardware Drivers but nothing shows up there. I know my computer has a small BIOS issue but I've used wireless on Ubuntu (wubi install) before and it worked fine after enabling hardware drivers. 
Can anyone help me?
Perhaps there is some terminal command I can enter to get ubuntu to scan for connected hardware or something.
It isn't imperative I get my wireless working, just something I'd like to accomplish.

Astrotrain12
[/SIZE]

---

### Post by samantha_ on 2010-02-01
> **astrotrain12 said:**
> [SIZE=2]I just installed 9.10 using Wubi onto a separate partition of my C drive on my HP Pavilion DV9700 laptop. I have a AMD TurionX2 64 bit processor. The wireless works when in Windows but not in Ubuntu. I tried going to SYSTEM>Admin>Hardware Drivers but nothing shows up there. I know my computer has a small BIOS issue but I've used wireless on Ubuntu (wubi install) before and it worked fine after enabling hardware drivers. 
Can anyone help me?
Perhaps there is some terminal command I can enter to get ubuntu to scan for connected hardware or something.
It isn't imperative I get my wireless working, just something I'd like to accomplish.

Astrotrain12
[/SIZE]

whats your broadcom card model.
If its a BCM4311-, BCM4312-, BCM4321-, or BCM4322 chipset, click below....

[[Click here to install Drivers]]("apt://bcmwl-kernel-source,bcmwl-modaliases")

---

