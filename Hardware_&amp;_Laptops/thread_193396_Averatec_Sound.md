---
title: "Averatec Sound"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by protito on 2006-06-09
Hi i have a 3270eh1 averatec laptop... and i remember sound working with ubuntu ina previous installation now i cant get it to work... if someone had the same problem with similar hardware and can help me.. it looks like it recognize the card but i t doesnt sound :(

ty

---

### Post by protito on 2006-06-10
ok i remember now...
iused live noapic nolapic acpi=off
that fixed kernel panics and sound...
i hope that helps suffering form kernel panics hehe

---

### Post by msofer on 2006-06-10
I am also using a 3270, and do not disable apic, lapic nor acpi. Especially the last is maybe too extreme? Don't you lose the powernowd functionality, and have your processor running all the time at full speed? That could cause thermal problems.

In any case, I sometimes do not have sound on bootup - it is somewhat random. But I always have sound after resuming from hibernation, and that is my normal procedure anyway.

---

