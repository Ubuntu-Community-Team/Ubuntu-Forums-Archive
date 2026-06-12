---
title: "My K6 2/550 system hangs up when using AGP card"
date: 2005-01-16
forum: Hardware &amp; Laptops
---

### Post by Serengeti on 2005-01-16
Hello,
I've build a computer of a "typewriter" kind for my dad using A-Trend ATC 5220 motherboard, K6-2 550 processor and Matrox G200 gfx card. The problem is, ubuntu halts at strange moments - sometimes during the bootup sequence, sometimes in gdm, sometimes after couple of minutes of work. Lockup always looks the same way, the system just freezes and responds to nothing but the reset button. I've run memtest, checked hdd for bad sectors, no errors at all. The problem is the same when I replace Matrox with Radeon VE, but stops when I try S3 Virge, pci version.  So I reckon it has something to do with the agp port. I remember running windows 2000 on this system, no blue screens/freezes whatsoever. Thanks for the tips :)

EDIT: Kernel option acpi=off helped. It seems everything's ok now.

---

