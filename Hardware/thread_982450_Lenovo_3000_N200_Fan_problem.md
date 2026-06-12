---
title: "Lenovo 3000 N200 Fan problem"
date: 2008-11-14
forum: Hardware
---

### Post by zambers on 2008-11-14
I'm running Ubuntu 8.10 (Intrepid Ibex) on a Lenovo 3000 N200, almost everything is doing fine, except for the fan.

When recovering from a suspended session the fan slowly fades out until a total halt, processor temps go high as hell. 

The only solution is to do a fresh restart. In this case the fan works the normal way.

Every suspended session causes this issue. Hibernation works fine.

Is any solution to make the fan go steady when recovering a suspended session?

---

### Post by zambers on 2008-11-15
bonk. sorry.

---

### Post by zambers on 2008-11-16
Bump!

---

### Post by Sagiv on 2009-05-26
Happened to me too. running Ubuntu 9.04 kernel 2.6.28-12-generic on Lenovo 3000 n200.
Does anyone know what causes this?

---

### Post by peppertarts on 2009-07-22
I have the same problem in Jaunty. The fan works fine up until you resume from hibernation then it stops and causes the laptop to overheat. There are no clues in the kernel messages as to what may be causing it and the fan isn't accessible in /proc/acpi/fan. Does anyone know of any potential fixes for this ACPI issue?

---

### Post by tp21 on 2009-08-01
are you sure you are using NVIDIA driver? try to go to System - Administration - Hardware Drives and choose the recommended driver.
good luck

---

### Post by felipebm on 2010-04-19
This is a well known hardware problem, and it is well documented in lenovo's forums:

[http://forums.lenovo.com/t5/Lenovo-3000-and-Value-line/3000-N200-Fan-problem/m-p/224150](http://forums.lenovo.com/t5/Lenovo-3000-and-Value-line/3000-N200-Fan-problem/m-p/224150)

I've tried updating the BIOS as well as cleaning throughly and it hasn't functioned.

---

