---
title: "HP 6910p ubuntu doesn't see bluetooth adapter."
date: 2012-10-08
forum: Hardware
---

### Post by keksior on 2012-10-08
Ubuntu 12.04, KDE4. I've got enabled bluetooth in my bios. But my Ubuntu doesn't see this adapter. Hcitool dev shows no devices. What can i do to get bluetooth working? Please i need it to my bluetooth headphones.

---

### Post by keksior on 2012-10-09
Anyone ? Please i need to et this bluetooth working on my kubuntu :(

---

### Post by keksior on 2012-10-10
Problem solved. The BT was soft disabled. I've enabled it using:
```
rfkill unblock bluetooth
```.

---

