---
title: "Scan hd for errors?"
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by freddan on 2005-12-04
I would appreciate if someone could give me a clue on how to scan my hd for bad clusters.

Thx..

---

### Post by Qrk on 2005-12-04
Its done automatically ever thirty boots, but if you want to do it on command, 

```
fsck -f
```

which forces the check.

---

### Post by davidsrsb on 2005-12-07
The smartmontools package is your friend as you need to see the S.M.A.R.T. statistics.
Modern drives hide bad sectors from the OS until they are on the point of death.

---

### Post by freddan on 2005-12-07
Thanks, I will have a look at that...

Rgds,
/F

---

