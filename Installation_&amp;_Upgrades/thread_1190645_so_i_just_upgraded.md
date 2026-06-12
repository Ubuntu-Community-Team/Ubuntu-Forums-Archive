---
title: "so i just upgraded"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by bsg221 on 2009-06-18
so i just up graded and it wont install the graphics driver wft 
any one how to fix

---

### Post by masux594 on 2009-06-18
Well, first of all, we need your grapic card specs.. Ati or NVidia? Graphic card name?

Sysc, A

---

### Post by Lampi on 2009-06-18
usually kernel headers are missing:

```

sudo apt-get install kernel-headers-'uname -r'
```

---

### Post by bsg221 on 2009-06-19
i end up switching back to intrepid 
but thanks for all the help

---

### Post by bsg221 on 2009-06-23
i use a nvidia graphics card
64 bit processor

---

