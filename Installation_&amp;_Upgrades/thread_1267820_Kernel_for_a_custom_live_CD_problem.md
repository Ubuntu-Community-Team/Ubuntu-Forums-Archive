---
title: "Kernel for a custom live CD problem"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by The_Phantom on 2009-09-16
Hi! I have a problem with a live cd customization... My kernel do not complete boot and exit in Busybox probably because it don't have all required modules to run in a live cd environment. Please, anyone know the modules kernel needed to run the kernel in a live cd? 

I already patch my kernel with the squashfs module (correct version) and unionfs module, but the cd don't boot. 

casper.log contains:
```

mount: Mounting unionfs on /root failed: No such device
unionfs mount failed

```

---

