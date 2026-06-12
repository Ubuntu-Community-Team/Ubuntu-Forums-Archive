---
title: "Ubuntu does not detect batter power level on HP nc6000"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by beamer_12 on 2008-02-24
I have just recently installed Ubuntu 7.10 on my hp nc6000 and everything seems to be working great except that it cannot detect the battery power level or how much time is left on the battery. The computer will just shut off after the battery dies. Is there any solution to this that anyone knows of?

---

### Post by fedex1993 on 2008-02-24
when you type acpci does it display anything after it at all?

---

### Post by beamer_12 on 2008-02-24
Says command not found

---

### Post by dicecca112 on 2008-02-24
type acpi the above post by fedex he mistyped acpi

---

### Post by beamer_12 on 2008-02-24
when i type in acpi it tells me the battery is at 100% and only has about a half hour left on it, it is an old computer so the batter life could be accurate, but what im worried about is that the computer can give no warning when it is running low on battery power, it simply shuts off. Is there a program that can monitor the battery life properly and give a warning when battery power is critically low.

---

### Post by TrD on 2008-05-08
I have the same problem. The acpi command returns: ```
Battery 1: charged, 100%
```

The tray applet says 9% charged, 450 hours until fully charged.

Is there a solution for this?

---

