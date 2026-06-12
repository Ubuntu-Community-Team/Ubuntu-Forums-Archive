---
title: "Is there any way to force the HD to spindown?"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by avilella on 2006-09-14
Hi all,

I have a computer with Ubuntu Dapper installed that I use to glance my email every once in a while during the day.

I made sure that laptop-support worked so that, when the computer has been idle for a while, the harddrive will spindown to halt, and will only turn back on after I use the computer again.

But I would likt to be able to force the HD to spindown at will (probably using a key combo). Does anybody know how to do that?

Is this laptop-support related? Or acpi related?

Thanks in advanced.

---

### Post by biophysics on 2006-09-15
There is certainly way to spin down your hard disk but I WARN you not to do it. (see man hdparm)

1. hard disks have only limited spin up and down counts.
2. It makes more sense to keep them running than spin them down

Read this file CAREFULLY so you will know:
/usr/src/linux/Documentation/laptop-mode.txt

---

