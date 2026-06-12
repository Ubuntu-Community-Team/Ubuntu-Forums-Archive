---
title: "System Beep"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by icer22x on 2007-11-20
So I open Xubuntu and go to /etc/modprobe.d/blacklist. How do I blacklist the system beep in here?
I tried just typing:

blacklist pcspkr

But it won't save and gives me an error.
Help? Thanks

---

### Post by papercut on 2007-11-20
Try editing

/etc/rc.local

add the line

```
modprobe -r pcspkr
```

before the line with exit 0

---

