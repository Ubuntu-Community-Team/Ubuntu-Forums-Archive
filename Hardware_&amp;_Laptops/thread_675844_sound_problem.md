---
title: "sound problem"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by harivadakara on 2008-01-23
i installed ububtu in my hp 520 but no sound from where i get firmware for intel 82801g?audio driver is not detecting in my system.can any one knows how to fix this problem?pls help me

---

### Post by eggdeng on 2008-01-23
Post the output of ```
lshw -C sound
``` and ```
aplay -l
```
That's lowercase L, not 1.

---

