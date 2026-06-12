---
title: "MP-BIOS bug: 8254 timer not connected to IO-APIC in Ubuntu Feisty"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by arijel on 2007-04-25
I have installed Ubuntu feisty on my laptop HP nx6325 (AMD Turion TL-52 x2) and when the system boots I get error message MP-BIOS bug: 8254 timer not connected to IO-APIC. Everything is working normal - I didn't notice any malfunction yet, but I'm curious in what is causing this problem and how can I make the error message go away :) .

---

### Post by horace on 2007-04-25
I was getting the same message, usually with no obvious effect, but then started getting kernel panic on boot. Adding noapic to the kopt line in /boot/grub/menu.lst fixed it, but I've no idea what this is about! I would be interested to know too.

---

### Post by arijel on 2007-04-25
I tried with the noapic parameter and the error disappeared but I still want to find out what's the cause of the problem because I'm sure that when I was running Edgy on the same laptop this error didn't appear.
Where can I read more on acpi and noacpi and other related parameter to better understand the hole process?

---

