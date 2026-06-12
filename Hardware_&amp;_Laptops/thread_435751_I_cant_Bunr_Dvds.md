---
title: "I cant Bunr Dvds"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by fathefner on 2007-05-07
What is a good DVD burning Software?  I cant burn DVD's other than that Ubuntu is all good.

---

### Post by ahaslam on 2007-05-07
> **fathefner said:**
> What is a good DVD burning Software?  I cant burn DVD's other than that Ubuntu is all good.

Have you tried Gnomebaker?
Many would suggest K3b, though that'll install half of KDE - depends on your drive space I suppose.

If you want to get your hands dirty, try the cli:

```
growisofs -dvd-compat -Z /dev/sr0=/path/to/.iso
```

;)

---

