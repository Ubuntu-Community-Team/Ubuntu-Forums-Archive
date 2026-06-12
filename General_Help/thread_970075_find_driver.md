---
title: "find driver"
date: 2008-11-03
forum: General Help
---

### Post by gishaust on 2008-11-03
hi

Is there a way from the terminal to find out what my display card is?

gishaust

---

### Post by mshipman on 2008-11-03
Open a terminal and type "lshw" (without the quotes).

---

### Post by Yellow Pasque on 2008-11-03
lshw should be run as root. I would recommend running update-pciids before listing the hardware on newer systems. Also, using -C display provides more specific info
```
sudo update-pciids
sudo lshw -C display
```

---

