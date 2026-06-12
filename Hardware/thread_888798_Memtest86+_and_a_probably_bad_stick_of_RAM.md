---
title: "Memtest86+ and a probably bad stick of RAM"
date: 2008-08-13
forum: Hardware
---

### Post by EmperorSquirrels on 2008-08-13
I've been having Windows trouble lately (currently on Ubuntu 8.04 because for some reason I get less blue screens) and I think I may have narrowed it down to my RAM. I did a memtest overnight and was wondering if it's possible to read the error message output or if I just have to trial-and-error to see which stick (or slot) is defective?
```

Tst                    7
Pass                   3
Failing Address        00071745874 - 1815.3mb
Good                   e996d087
Bad                    e9d6d087
Err-Bits               00400000
Count Chan             1
```

---

### Post by jimv on 2008-08-13
I'd pull a stick out and run memtest again.  It's the best way to be sure which stick is bad.

---

### Post by pietjanjaap on 2008-08-13
1 failing adress is not good.
Try 1 and the the other 1.
If both are ok wenn testing alone, then check how much voltages is on de memory stick(wenn pc is running). Then look at the manufacturer off the memory how much voltages is allowed for this memeory. Then if possible increase the voltages with small steps.
And test again.

---

