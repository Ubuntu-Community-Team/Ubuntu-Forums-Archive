---
title: "laptop won't boot on battery. freezes at &quot;hardware drivers&quot;"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by rumo_orbis on 2007-11-24
i'm running xubuntu 7.10 on a inspiron 8600. my problem is that when i unplug the power cable my laptop won't boot anymore (strangly enough it will reboot though). 
i looked at the console output with pressing alt+f1 and i see it gets stuck at ```
loading hardware drivers
```
i already checked the following options... it doesn't have anything to do with the fglrx driver. noacpi boot parameters don't help. ```
ENABLE_LAPTOP_MODE=true
``` doesn't help either...

i also get the ```
intel_rng: FWH not detected
``` error. but blacklisting it doesn't change anything, so i guess it's not related.

it's really annying... i'm supposed to have a laptop, but can't use it without wall power. i would be really glad if anyone could help me!

rumo

---

### Post by rumo_orbis on 2007-11-24
bump

---

### Post by rumo_orbis on 2007-11-24
now i replicated the same error in recovery mode. it froze at something with "Yenta TI"...

---

### Post by rumo_orbis on 2007-11-25
bump

---

### Post by rumo_orbis on 2007-11-25
i noticed that it doesn't actually always freeze at the exactly same point. but it is always either right after or shortly after:
```
APCI PCI Interrupt Link enabled at IRQ 7
APCI PCI Interrupt 0000:02:03:0[A] -> Link -> GSI 7 (level, low) -> IRQ 7
```

---

### Post by rumo_orbis on 2007-11-25
ok... i managed to fix it... stumbled over a post where it said i had to change something in the bios from (in my case) "minimal" to "thorough"...

---

### Post by maka on 2007-12-01
could you give me the details on how you fixed this?  I am experiencing the same frustrating issue. thanks in advance

---

### Post by rumo_orbis on 2007-12-01
i had to change the option "boot post" in my bios to "thorough". hope that helps!

---

