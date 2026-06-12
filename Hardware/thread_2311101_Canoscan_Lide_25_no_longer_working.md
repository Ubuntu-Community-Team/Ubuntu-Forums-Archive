---
title: "Canoscan Lide 25 no longer working?"
date: 2016-01-24
forum: Hardware
---

### Post by eezacque on 2016-01-24
The scanner worked 3 days ago, there is always a small chance it has passed away, but I would like to spend a little more time with it.
It is listed through lsusb, and sane-find-scanner, but Simple Scan says there are no scanners detected...

Any clue?

---

### Post by ajgreeny on 2016-01-24
Install xsane if you don't have it and try that.

---

### Post by eezacque on 2016-01-24
> **ajgreeny said:**
> Install xsane if you don't have it and try that.

Same problem: no devices available

---

### Post by eezacque on 2016-01-24
Just found my saned service is inactive (dead).

Any clue?

---

### Post by eezacque on 2016-01-25
Going back to 3.19.0-44 solved the problem.
Under 3.19.0-43 sane believes the device is busy.
I'll file a bug report.

---

