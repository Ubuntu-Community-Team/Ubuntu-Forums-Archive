---
title: "Can't resize partition!"
date: 2008-08-25
forum: General Help
---

### Post by cablejimmy on 2008-08-25
I cannot resize the main partition on my laptop. When I use an ubuntu live cd, with gparted, it starts but crashes with an error without actually doing anything. I'll post what the error says soon.

---

### Post by dmizer on 2008-08-25
Try killing the hardware activation layer daemon with this command:
```
sudo killall hald
```

Then try to resize the repartition.

---

