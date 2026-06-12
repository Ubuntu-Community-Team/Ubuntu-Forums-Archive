---
title: "X220 i7 doesn't suspend"
date: 2011-08-04
forum: Hardware
---

### Post by da7oom on 2011-08-04
Hey

when i installed ubuntu 11.4 on my x220 suspend was working out of the box, but now it's not

when i put the machine in suspend mode, power button start blinking and either caps lock button, and all system hang.

i followed this bug thread but nothing worked for me 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998) 

your help is much appreciated.

---

### Post by da7oom on 2011-08-05
Anyone ?

---

### Post by Toz on 2011-08-05
Sounds like a kernel panic during suspend. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1809958]("http://ubuntuforums.org/showthread.php?t=1809958").

Can you boot an earlier kernel and see if suspend works?

---

### Post by da7oom on 2011-08-05
> **Toz said:**
> Sounds like a kernel panic during suspend. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1809958]("http://ubuntuforums.org/showthread.php?t=1809958").

Can you boot an earlier kernel and see if suspend works?

Thanks !

turn out that virtualbox 4.1 causing  this problem 

i removed it and every thing went good !

---

