---
title: "Errors when I hibernate?"
date: 2009-08-08
forum: Hardware
---

### Post by nathan726 on 2009-08-08
Just before my laptop goes into hibernation I get something similar to the following:
```
[######.######] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[######.######] ata2: irq_stat 0x40000001
```(where '#' are some numbers) Does anyone know what these errors mean? How I can fix them?

---

### Post by nathan726 on 2009-09-29
Bump. Anyone know what they are? Is it normal to see that when I shutdown?

---

### Post by QIII on 2009-09-29
What version of Ubuntu are you using and what kernel version?

You can get a verbose bit of info for me about the OS and kernel version by 

```
uname -a
```

There was a regression in at least one kernel (On the Debian side that I know of.  Not sure if it affected Ubuntu directly.)

---

### Post by nathan726 on 2009-10-01
uname -a
```
Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
```

The errors don't have any noticeable effect on my pc, so is it safe to just ignore them?

---

### Post by desmane on 2009-10-01
yes, just ignore them. And never touch a running system anyway :)

---

