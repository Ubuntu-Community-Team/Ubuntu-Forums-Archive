---
title: "[HOW TO] Resolve Ubuntu freezing in LG LW65/LW75 (disable pcspkr)"
date: 2009-02-22
forum: Hardware
---

### Post by bluryfusion on 2009-02-22
This Problem, is caused by system beep, to disable this one, you should blacklist the module, running:
```
sudo modprobe -r pcspkr
sudo echo -e "\nblacklist pcspkr" >> /etc/modprobe.d/blacklist
```

This removes system beep module, and disable pcspkr, now you could use backspace and tab keys, even in console mode.
This bug that affected many laptop models, is solved since karmic.

---

