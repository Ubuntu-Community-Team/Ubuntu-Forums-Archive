---
title: "Processor family for Core 2 Duo?"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by ronlybonly on 2007-01-26
I am looking to compile the latest stable linux kernel from kernel.org, and I was wondering what processor family architecture to select during the kernel configuration for my Intel Core 2 Duo. Thanks for any help you could give me!

-Andrew

---

### Post by Stemp on 2007-01-26
I think it's Pentium IV with SMP support.

---

### Post by ronlybonly on 2007-01-26
Thanks! I'll give that a shot.

---

### Post by dabl on 2007-01-26
If you have Core 2 Duo, you want this:

2.6.17-10-generic

---

### Post by usererror on 2007-02-02
> **dabl said:**
> If you have Core 2 Duo, you want this:

2.6.17-10-generic

Why Generic?  How can I tell on 6.10 if i'm actually utilizing my Duo Core?

---

### Post by Stemp on 2007-02-02
```
cat /proc/cpuinfo
```

BTW this thread was talking about compiling your own kernel.
But the 2.6.17-generic replace the smp kernels, so your core duo is recognized ;)

---

