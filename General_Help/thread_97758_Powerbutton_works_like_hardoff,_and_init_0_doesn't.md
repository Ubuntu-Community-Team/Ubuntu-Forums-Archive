---
title: "Powerbutton works like hardoff, and init 0 doesn't shutdown completely!"
date: 2005-12-01
forum: General Help
---

### Post by daller on 2005-12-01
Hi There,

After an upgrade (a long time ago), my powerbutton stopped working as in an ATX pc, but like the old AT pc's (Hardoff)

Using "init 0", it leaves me with a line saying "Power Down" (and something more) in the terminal - And I can then Hardoff...

Any ideas?

---

### Post by 23meg on 2005-12-02
Maybe ACPI isn't working. See if you have a /proc/acpi entry and check if other ACPI options work.

---

