---
title: "Duo Core Support"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by rajeshrs on 2006-07-14
Is the kernel which comes with Ubuntu (the latest versions of live and installer CDs) ready for use with Intel Core Duo processors? Or will it function like Windows XP - in that it will be able to use it much like a conventional solo core processor? I believe Vista has core duo support.

--Rajesh

---

### Post by Jagot on 2006-07-14
You will need to install the smp to properly take advantage of it.  The kernel supplied with Ubuntu does not support dual core, hyperthreading, etc - it will just run them as a normal solo processor.

```
sudo aptitude update && sudp aptitude install linux-686-smp
```

---

### Post by Frank Golden on 2006-07-20
> **rajeshrs said:**
> Is the kernel which comes with Ubuntu (the latest versions of live and installer CDs) ready for use with Intel Core Duo processors? Or will it function like Windows XP - in that it will be able to use it much like a conventional solo core processor? I believe Vista has core duo support.

--RajeshAs far as I know XP supports core duo also.

---

