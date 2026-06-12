---
title: "nc8000 brightness controls"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by jjstautt on 2006-07-17
I am trying to get the brightness controls working on a HP Compaq nc8000 laptop with Dapper. Has anyone had success with this that could suggest a solution? Google is not being very helpful for me today.

---

### Post by Jagot on 2006-07-17
I have no experience with that laptop, but if you cannot find a solution specific to it then you could always use xgamma from Terminal:

```
xgamma -gamma 0.8
```

1.0 is the default.  Lower the number to decrease brightness, increase to brighten.

---

