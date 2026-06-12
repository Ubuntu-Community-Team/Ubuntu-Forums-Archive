---
title: "64 bit install - please verify it took"
date: 2014-12-03
forum: Hardware
---

### Post by michael-piziak on 2014-12-03
Just making sure my 64 bit install worked.

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               2800.000
BogoMIPS:              5586.04
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
NUMA node0 CPU(s):     0,1
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by Yellow Pasque on 2014-12-03
lscpu tells you of the capabilites of the cpu. uname would be more insightful:
```
uname -a
```

---

### Post by michael-piziak on 2014-12-03
> **Temüjin said:**
> lscpu tells you of the capabilites of the cpu. uname would be more insightful:
```
uname -a
```


michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ uname -a
Linux michael-HP-Compaq-dc5800-Small-Form-Factor 3.13.0-40-generic #69~precise1-Ubuntu SMP Fri Nov 14 10:29:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by Yellow Pasque on 2014-12-03
Yeah, it's 64-bit.

---

### Post by michael-piziak on 2014-12-03
Thanks so much!

Marking this thread as solved.

---

