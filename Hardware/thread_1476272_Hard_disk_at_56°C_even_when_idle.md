---
title: "Hard disk at 56°C even when idle"
date: 2010-05-07
forum: Hardware
---

### Post by ishijoe on 2010-05-07
My hard disk is, even when my laptop is idle.  Can anyone help me to reduce the temperature.
I have made some research and have found the hdparm command. I was thinking to set my spin-down time but then i see that my APM is at 254. In the hdparm's man it says that if the APM is btw 128 and 254 then spin-down is not permit. It is as follows:
```

       -B     Query/set Advanced Power Management feature, if the  drive  sup&#8208;
              ports  it.  A  low value means aggressive power management and a
              high value means better performance.   Possible  settings  range
              from  values  1 through 127 (which permit spin-down), and values
              128 through 254 (which do not permit  spin-down).   The  highest
              degree  of power management is attained with a setting of 1, and
              the highest I/O performance with a setting of 254.  A  value  of
              255 tells hdparm to disable Advanced Power Management altogether
              on the drive (not all drives support disabling it, but most do).
```

I hope I understood well and I will like any help in the best way how to solve my issue.

---

