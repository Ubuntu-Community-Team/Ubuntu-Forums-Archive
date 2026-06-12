---
title: "ACPI Issues"
date: 2008-08-30
forum: Hardware
---

### Post by .Garrett on 2008-08-30
I'm having a bit of a problem...

Whenever I shutdown through the quit menu, it simply goes to a black screen as if my monitor were off, and hangs. I read somewhere adding acpi=off to the menu.lst file would fix it, and it did. However, that quite obviously disables ACPI, and doing that fixes shutdown, but removes a bunch of other stuff such as suspend and restart.

Is there any way I can fix the shutdown problem without using acpi=off?

---

### Post by nicedude on 2008-08-30
Yes I believe so if you just turn off suspend and hibernate but leave menu.lst boot commands alone. I don't use either myself as they are finicky and cause me problems so out they go :-)

---

