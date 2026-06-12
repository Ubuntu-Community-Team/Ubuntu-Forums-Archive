---
title: "Scanner not working"
date: 2021-02-12
forum: Hardware
---

### Post by jmichaels29 on 2021-02-12
HP Laserjet Pro MFP M127fn printer/scanner combo.
Printer part does work.

"Document Scanner" app searches for and finds scanner, but then when I scan it says it can't connect to scanner.

---

### Post by brian_p on 2021-02-14
> **jmichaels29 said:**
> HP Laserjet Pro MFP M127fn printer/scanner combo.
Printer part does work.

"Document Scanner" app searches for and finds scanner, but then when I scan it says it can't connect to scanner.

Ubuntu 20.04? USB connected? Let's see why printing works. Give ```
lpstat -t
```

---

### Post by jmichaels29 on 2021-02-17
Fixed by:

$ sudo apt install hplip hplip-gui
and then
$ hp-setup

---

