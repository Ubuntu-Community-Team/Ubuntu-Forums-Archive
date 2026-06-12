---
title: "Identifying keyboard hot keys commands"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by sagara on 2008-03-16
Is there any tool out there that shows me what commands my keyboard sends to the X server?
Im looking for a similiar tool like **xev** (tracks mouse events) but for keyboards.  Does it exist?

---

### Post by solar george on 2008-03-16
Xev also lists keyboard events.

---

### Post by piousp on 2008-03-16
Try

```
lshal -m
```

---

### Post by sagara on 2008-03-18
> **solar george said:**
> Xev also lists keyboard events.

You are right, xev monitors keyboard strokes as well.
I noticed that there are some hot keys on my keyboard that not even xev detects (i have a joystick keypad for example).  Does that mean that unix doesn't recognize those keys at all?

---

