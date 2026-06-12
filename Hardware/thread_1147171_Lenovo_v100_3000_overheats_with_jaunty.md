---
title: "Lenovo v100 3000 overheats with jaunty"
date: 2009-05-03
forum: Hardware
---

### Post by mistlur1 on 2009-05-03
Whenever I boot jaunty with a 2.6.28-* kernel the cpu-temp gets progressively higher (even when idle) and when reaching 100 degrees C the computer does an emergency powerdown. This is in spite of the cpu-fan spinning at a high rpm from start.
When using a 2.6.27-* kernel heat is not as much of a proplem, this computer has always been "hot", running around 60 degrees C, and thats also what I read when booting jaunty with the intrepid kernel. The intrepid kernel doesn't allow cpu freq scaling though.

This is from the log:
```
May  3 13:05:54 sture kernel: [ 1296.158572] ACPI: Critical trip point
May  3 13:05:54 sture kernel: [ 1296.158589] Critical temperature reached (100 C), shutting down.
```

Anyone else having similar probplems? Any suggestions how to proceed, perhaps it's an acpi bug?

Any help appreciated

/mistlur1

---

### Post by bosmanoglu on 2009-06-21
Hey, I don't know if this helps but I found this on the web looking for the error: [http://bugzilla.kernel.org/show_bug.cgi?id=8713](http://bugzilla.kernel.org/show_bug.cgi?id=8713)
Response #20 has some important information I guess, but I haven't tried it yet. Good luck...

---

