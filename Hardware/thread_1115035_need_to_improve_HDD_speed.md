---
title: "need to improve HDD speed"
date: 2009-04-03
forum: Hardware
---

### Post by israelariel on 2009-04-03
i had installed ubuntu 8.04 and just bought a 500 Gb HDD SATA maxtor,  the speed of this HDD is about 1.0 Mb\s when a make a copy..... is that alright, can i improve this speed? any codecs is missing?
thanks

---

### Post by cariboo on 2009-04-03
Open an Applications-->Accessories-->Terminal and type:

```
sudo hdparm -tT /dev/sdx
```

where x is your 500Gb hard drive. Could you paste the output in your next post.

Jim

---

### Post by the8thstar on 2009-04-03
Mine is here:

> the8thstar@the8thstar-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:

 Timing cached reads:   2168 MB in  2.00 seconds = 1084.96 MB/sec
 Timing buffered disk reads:  112 MB in  3.05 seconds =  36.78 MB/sec


to give the OP a base for comparison.

---

