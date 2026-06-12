---
title: "intel_rng: FWH not detected"
date: 2008-09-08
forum: General Help
---

### Post by strattonbrazil on 2008-09-08
When booting, it times out while doing something with the clock:

intel_rng: FWH not detected

When a menu pops up like GRUB, the timer doesn't decrement like it used to.  I've tried putting FreeBSD on this machine, but it also locks up at a clock stage:

Calibrating clock(s)

but I don't think there's a timeout for FreeBSD.  Does anyone know what causes this?  I have a Super Micro X7DA8 motherboard.  

Thanks.

---

### Post by rmmartins on 2008-09-09
Had this problem too, refer to [here]("http://ubuntuforums.org/showthread.php?t=894131&highlight=intel_rng").

---

