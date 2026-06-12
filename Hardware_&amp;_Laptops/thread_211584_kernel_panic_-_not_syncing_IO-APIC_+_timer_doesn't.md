---
title: "kernel panic - not syncing: IO-APIC + timer doesn't work!"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by blindspy on 2006-07-08
Booting my dual core macbook with the new 2.6.15-25-686 #1 SMP PREEMPT. I get this error while booting **itermitantly**:

```
kernel panic - not syncing: IO-APIC + timer doesn't work!
```

I've searched around quite a bit but I was only able to find developer mailing list posts that dont give any solutions:

[http://lkml.org/lkml/2006/2/9/257]("http://lkml.org/lkml/2006/2/9/257")

---

### Post by phico on 2006-07-10
I also get this error but not very often.
I tried with othe kernel and kernel configs but I could not get rid of it ..

---

### Post by sglynnsp on 2006-07-10
Same here. Setup the macbook following instructions on [http://bin-false.org](http://bin-false.org). Doesn't happen always, just once say every three reboots. Also sometimes get a blank screen with no activity after selecting linux from the refit menu. Again random, but happens less frequently than the kernel panics.

---

### Post by blindspy on 2006-07-10
I emailed a few kernel devs and got some respondses so I filed a Ubuntu bug report:
[https://launchpad.net/bugs/52553](https://launchpad.net/bugs/52553)

---

