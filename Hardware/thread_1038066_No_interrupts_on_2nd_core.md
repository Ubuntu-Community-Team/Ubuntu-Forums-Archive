---
title: "No interrupts on 2nd core"
date: 2009-01-12
forum: Hardware
---

### Post by kingfisher on 2009-01-12
Hi,

using mpstat I found out that the 2nd core of my cpu doesn't receive any interrups, the output is:

```
18:11:11     CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
18:11:11     all   10.50    0.13    5.86    2.92    0.04    0.09    0.00   80.46    442.63
18:11:11       0   10.80    0.15    5.95    3.12    0.08    0.18    0.00   79.72    236.99
18:11:11       1   10.20    0.12    5.77    2.73    0.00    0.01    0.00   81.18      0.00
```

On other systems, each core gets interrupts to handle, so what does this mean on my system? Is the core broken?

Greetings,
Christian

---

