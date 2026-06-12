---
title: "32/64 bit question"
date: 2014-12-02
forum: Hardware
---

### Post by michael-piziak on 2014-12-02
Does this mean I'm running 32 bit like I think - I typed  lscpu into terminal and got:

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               1596.000
BogoMIPS:              5585.87
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by slickymaster on 2014-12-02
> **michael-piziak said:**
> Does this mean I'm running 32 bit like I think - I typed  lscpu into terminal and got:

[COLOR=#ff0000][B]Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit[/B][/COLOR]
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               1596.000
BogoMIPS:              5585.87
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

That tells you that you have a 64-bit CPU running a 32-bit Linux version.

---

### Post by michael-piziak on 2014-12-02
Thanks.  I'm on the fence on trying to decide if a 64 bit version will benefit me.  Some users say yes, while some say it's a misconception.

Marking this thread as solved.

---

