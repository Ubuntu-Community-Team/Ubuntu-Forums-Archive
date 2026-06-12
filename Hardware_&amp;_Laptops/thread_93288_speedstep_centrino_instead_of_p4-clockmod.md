---
title: "speedstep_centrino instead of p4-clockmod"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by series on 2005-11-21
```
#dmesg | grep freq
Warning: Pentium M detected. The speedstep_centrino module 
offers voltage scaling in addition of frequency scaling. You should 
use that instead of p4-clockmod, if possible.
```

I use the kernel 2.6.14

In the kernel config, I don't know which post is the centrino_speedstep. Can this be it:

```
Intel Speedstep on ICH-M chipsets (ioport interface)
```

When I choose it instead of the p4-clockmod, the freq-scaling won't work at all.

---

### Post by benguin on 2005-11-21
Hey there
You'll need the Enhanced speedstep option as a module or built into the kernel. Not the ICM-whatever module.

---

