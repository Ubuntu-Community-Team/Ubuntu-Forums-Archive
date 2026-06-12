---
title: "ac connect/disconnect not noticed"
date: 2006-05-23
forum: Hardware &amp; Laptops
---

### Post by torben81 on 2006-05-23
I'm running breezy on a MSI S260 Laptop with 2.6.12-10 kernel.
When I connect or disconnect the AC, klaptop does not notice the change.

When booting, however, the state is correctly determined and in case of battery  use speedstepping etc. works fine as configured for klaptopdaemon.

When plugging in the AC I get the following message in /var/log/messages:
```
atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
```

Unplugging causes:
```
atkbd.c: Unknown key pressed (translated set 2, code 0xf2 on isa0060/serio0).
```

Any ideas?
Thanks, Torben

---

