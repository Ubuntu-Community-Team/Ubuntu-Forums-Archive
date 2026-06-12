---
title: "Ubuntu Server - Multiple cpu support"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by Tranquil on 2007-06-10
Hello,

Anyone knows if ubuntu server supports more than 2 cpu's ? 
and if so, which version?

10x.

---

### Post by neptho on 2007-06-10
```
%grep CONFIG_NR_CPUS /boot/config-2.6.20-1*-generic
/boot/config-2.6.20-15-generic:CONFIG_NR_CPUS=8
/boot/config-2.6.20-16-generic:CONFIG_NR_CPUS=8
```

The standard kernel supports 8; you can recompile with support for more if you need them.

---

