---
title: "how do i use gcc3.x with gcc4.x installed?"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by adamjspooner on 2006-01-12
Hello,

I'm trying to install QEMU, but it can only use gcc3.x.  I have both gcc3.x and gcc4.x installed...is there a way that when I type "make" i can specify gcc3?

Thanks,
Adam

---

### Post by 23meg on 2006-01-12
Before building, enter the following: ```
CC=gcc-3.4
export CC
```

---

