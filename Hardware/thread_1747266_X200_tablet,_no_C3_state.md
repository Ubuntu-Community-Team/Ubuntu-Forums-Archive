---
title: "X200 tablet, no C3 state"
date: 2011-05-02
forum: Hardware
---

### Post by lol24h on 2011-05-02
I wonder if it happened just after bios update to 3.17 or after fresh ubuntu install. I'am missing the most efficient frequency state:

```
 Twój procesor obs&#322;uguje nast&#281;puj&#261;ce C-states : C1 C2 C3 C4 C
Twój BIOS podaje nast&#281;puj&#261;ce C-states : C1 C2 C4 

Cn                &#346;rednia residency   P-stany (cz&#281;stotliwo&#347;ci)
C0 (CPU aktywny)        ( 9,2%)       Tryb Turbo     0,0%
polling           0,2ms ( 0,0%)         1,87 GHz     0,0%
C1 mwait          0,0ms ( 0,0%)         1,60 GHz     3,3%
C2 mwait          0,3ms (12,6%)          800 MHz    96,7%
C4 mwait          1,9ms (78,2%)

```

Why is there polling in 1,87Ghz mode ?
I will install Windows and check whether happens the same, any ideas ? I defaulted BIOS.

*uname -a* shows:
```
Linux purr 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux
```

kernel from propesed repository, I tried this one after I noticed the same in stable rep.

---

