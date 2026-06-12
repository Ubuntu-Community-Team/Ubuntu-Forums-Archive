---
title: "Optimising system performance with encrypted drives in RAID"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by iTrickU on 2008-12-16
Hi,

Would the system perform better if i install linux onto an encrypted (luks) raid partition that was on a hardware raid controller (not fake raid, raid 1 or 5) or used software raid (md raid, raid1)? 

I am asking because if i use luks for encryption, its pulling the info through the cpu, so i figured why not get it to do the raid part as well, it should cause minimal extra usage and the kernel can optimise the read/write operations to maximise performance

But if i used hardware, the kernel will not have a chance to optimise the read/writes because it will not know whats happening on the drives themselves.

Not at all sure on this, can someone clear things up? thanks

(also if there isn't much to gain from hardware i will go with software since i don't want to be finding a new controller if this one fails)

---

