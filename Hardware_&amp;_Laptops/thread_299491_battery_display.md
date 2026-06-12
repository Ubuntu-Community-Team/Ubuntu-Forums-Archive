---
title: "battery display"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by a_dejot on 2006-11-14
hello everybody - i am pretty new to (x)ubuntu, installed a couple of days ago on my laptop. overall i am very satisfied; the battery display, however, does not seem to work properly (i constantly get 0%). it recognizes when the AC is plugged in and displays the cpu temp correctly - only the battery status is constantly 0% with remaining time 00:00. UPDATE: this problem only occurs when booting with the power cable plugged in - if i boot with battery only, the battery percentage is shown correctly - remaining time still constantly at 00:00.

btw (i don't know if this is in direct connection to the above problem): i tried patching DSDT and get 7 warnings (number 1103) of the following type:

```

DSDT.dsl  3931:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

```

any ideas?

thanks in advance

---

### Post by a_dejot on 2006-11-18
...even though i search the web rather thoroughly, i couldn't find a solution for the above warning... still hoping anybody out there has/had the same problem! :)

---

### Post by anagor on 2007-12-26
It seems that the solution to get rid of the warning is to change Acquire (MUTE,0xsomething) to Acquire(MUTE, 0xFFFF)

Took me awhile to find it.
and to answer :)

---

