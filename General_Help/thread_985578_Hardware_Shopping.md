---
title: "Hardware Shopping"
date: 2008-11-17
forum: General Help
---

### Post by Grant A. on 2008-11-17
Is there any command in Linux to find out my hardware specs everything from the motherboard to whether my HDD is IDE or SATA?

---

### Post by Yellow Pasque on 2008-11-17
Try (that's a capital i):
```
hdparm -I </dev id, e.g. /dev/sda>| grep SATA
```

You could also look in your BIOS/system setup.

---

### Post by Grant A. on 2008-11-17
> **Temüjin said:**
> Try (that's a capital i):
```
hdparm -I </dev id, e.g. /dev/sda>| grep SATA
```

You could also look in your BIOS/system setup.

Ah, Thank you for much for your help :)

---

