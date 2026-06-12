---
title: "Wifi cuts out whenever i hibernate or let the computer enter sleep mode"
date: 2011-08-26
forum: Hardware
---

### Post by Krakenofthesea on 2011-08-26
I was having issues with my internet cutting out due to conflicting drivers[solved], but i still havent figured out how to fix my issue with the wifi cutting out when my computer goes into sleep or standby mode. an ideas?

Krakenofthesea

---

### Post by chili555 on 2011-08-26
The wireless is supposed to cut out, in order to save battery power, when you sleep. I suspect what you really want is for it to spring to life when you resume. Please try:```
sudo gedit /etc/pm/config.d/config
```Add one line:

```
SUSPEND_MODULES="r8192e_pci"
```Proofread carefully, save and close gedit. You should be all set.

---

### Post by Krakenofthesea on 2011-08-26
Beautiful. Thanks so much!

---

### Post by chili555 on 2011-08-26
Are you ready to use thread tools at the top and Mark Solved?

---

