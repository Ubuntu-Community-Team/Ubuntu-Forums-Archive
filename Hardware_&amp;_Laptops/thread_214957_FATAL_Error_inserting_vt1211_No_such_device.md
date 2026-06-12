---
title: "FATAL: Error inserting vt1211: No such device"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by jostrn on 2006-07-13
Hi,

my laptop has a vt1211 hardware monitoring chip as sensors-detect reports:
```

Do you want to scan for Super I/O sensors? (YES/no):
Probing for `Nat. Semi. PC87591 Super IO'
  Success... but not activated
Probing for `VT1211 Super IO Sensors'
  Failed! (0xec)

Do you want to scan for secondary Super I/O sensors? (YES/no):
Probing for `VT1211 Super IO Sensors'
  Success... found at address 0x0c00

```Since current kernels don't have a vt1211 driver i compiled 2.6.14.2 with the patch from hem.bredband.net/ekmlar/vt1211.html.
When i try to load the module with *sudo modprobe -v vt1211* or *sudo modprobe -v vt1211 force_addr=0x0c00* i get:
```
FATAL: Error inserting vt1211 (/lib/modules/2.6.14.2/kernel/drivers/hwmon/vt1211.ko): No such device
```

Any suggestions? Unfortunately i'm an bloody noob in kernel affairs

---

### Post by TuxCrafter on 2006-07-18
standby please i will build a how to :cool:

---

### Post by TuxCrafter on 2006-07-18
since you are so far already maybe this will help:

updatedb
locate vt1211
depmod
insmod <dir to vt1211.ko>

and post te result

---

