---
title: "/sbin/modprobe abnormal exit on boot"
date: 2008-08-18
forum: General Help
---

### Post by shadowhywind on 2008-08-18
Hi, I am running Kubuntu 8.04 (Hardy) amd64 on an HP dv6000. Lately when i try to boot the boot freezes/goes to text only mode with this error message
```
udevd-event[4375]: run program: '/sbin/modprobe' abnormal exit
```

earlier in the week i fought with the above error and this one 
```
crc error
Kernel panic - not Syncing: VFS: Unable to mount rootfs on unknown-block(0,0)
```

I fixed that issue by updating my kernel (kernel 2.6.24-21-generic), and haven't ran into that error yet, not sure if it semi-related. So far i get the abnormal exit error about 2 out of every 3 boots, its starting to get a bit irritating. Also the boot options i have tried have been acpi_irq_balance, noapic irqfixup, noapic acpi_irq_balance. Nothing seams to work. I do not know what logs would be good to post. So if you need anything please just let me know, and i will post. Any help would be great.

---

