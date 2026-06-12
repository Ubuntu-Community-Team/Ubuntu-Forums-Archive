---
title: "Apic"
date: 2008-08-03
forum: General Help
---

### Post by Seller on 2008-08-03
Motherboard- m2n 570 sli deluxe

I see a lot of issues but cannot find a fix to this problem:

upon trying to install I get to the screen and it starts to install and halts on the error "Kernel panic not syncing MP bios bug 8254 timer not connected to IO- APIC" 

I looked up ACPI and all that fancy stuff but my mother board does not allow me to switch it off in the bios.  

Any help would be appericiated because I really want to use this software

ps. the unbuntu version is 6.06

---

### Post by spiderbatdad on 2008-08-03
try other options from the startup screen.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I think the option you want is noapic, and I recommend deleting quiet splash.

---

