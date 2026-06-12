---
title: "HDIO_Drive_CMD failed: input/output error"
date: 2008-05-04
forum: Hardware
---

### Post by Nonsense on 2008-05-04
Every now and then my Ubuntu freezes and then gives me a black screen with the following message:

```
/dev/sda1:
Setting Advanced Power Management level disabled
HDIO_Drive_CMD failed: input/output error

```I looked around the forum a bit and some suggest ```
hdparm -b 255
``` but that just gives me the same message as when the desktop crashes:
```

/dev/sda1:
Setting Advanced Power Management level disabled
HDIO_Drive_CMD failed: input/output error
```Suggestions?

---

### Post by panfist on 2008-11-16
I have the same problem.

---

### Post by Nonsense on 2008-11-16
It turns out that my problem was due to a faulty ram.
I pulled out the bad memory and my problems are gone.

Run memtest that comes with the Live CD and check yours.

---

### Post by gongjijiao on 2009-03-17
you can set 
hdparm -B 255 /dev/sda1
to turn off the advanced power management.

---

