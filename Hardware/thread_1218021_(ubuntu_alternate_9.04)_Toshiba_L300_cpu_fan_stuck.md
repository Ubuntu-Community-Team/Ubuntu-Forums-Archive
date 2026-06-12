---
title: "(ubuntu alternate 9.04) Toshiba L300 cpu fan stuck on"
date: 2009-07-20
forum: Hardware
---

### Post by g0nad on 2009-07-20
I'm using Ubuntu Alternate 9.04 on a Toshiba L300 and the CPU fan is stuck on full speed permanently.  It should only come on when it is needed, not all the time.  I don't know how to get it to behave normally, could someone please help me?

---

### Post by komputes on 2009-07-20
This thread and possibles fixes are being discussed on [http://ubuntuforums.org/showthread.php?t=1042500](http://ubuntuforums.org/showthread.php?t=1042500)

---

### Post by g0nad on 2009-07-22
the kernel boot option:

  acpi_osi="Linux" 

appears to have done the trick.

---

