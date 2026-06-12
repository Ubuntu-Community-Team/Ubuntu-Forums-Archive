---
title: "I don't have a standby button"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by theWrkncacnter on 2007-09-09
My computer doesn't have a standby option, even though standby works in windows. System>preferences>power management doesn't have anything useful in it. How can I obtain this functionality, or at least find out for sure if ubuntu supports standby on my hardware or not?

--theWrkncacnter

---

### Post by kidders on 2007-09-10
Hi there,

**cat /sys/power/state** will give you a list of the standby states your BIOS supports. If you don't have a sleep button on your chassis, you could always use xmodmap to bind the function to a key combination.

---

### Post by theWrkncacnter on 2007-10-24
$ cat /sys/power/state
standby disk 

does this mean hibernate?

---

### Post by kidders on 2007-10-24
It does, yes. "Disk" (sometimes called "S4" ... ie sleep state #4 ... in ACPI documentation) is what is commonly referred to as "hibernate".

---

