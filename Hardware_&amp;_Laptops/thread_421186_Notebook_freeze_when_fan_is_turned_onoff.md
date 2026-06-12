---
title: "Notebook freeze when fan is turned on/off"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by georg.schw on 2007-04-24
Hi,

i've a problem with my notebook (Compaq Evo N620C). Everytime when the fan is turned on or off the whole notebook freezes for about a second.

On edgy i could fix this prolem with a new kernel pakage (2.6.19). Now i have feisty and kernel 2.6.20 and the same problem is here again.

Anyone an idead how to fix this problem? Thanks.



this appears in /var/log/acpid
```

[Tue Apr 24 14:33:49 2007] received event "thermal_zone TZ1 00000081 00000000"
[Tue Apr 24 14:33:49 2007] notifying client 4597[107:112]
[Tue Apr 24 14:33:49 2007] notifying client 5013[0:0]
[Tue Apr 24 14:33:49 2007] completed event "thermal_zone TZ1 00000081 00000000"

```

---

### Post by adrss on 2007-05-04
i have the same problem. i uninstalled powernod and installed powersaved, and the freezes become less anoying.

---

