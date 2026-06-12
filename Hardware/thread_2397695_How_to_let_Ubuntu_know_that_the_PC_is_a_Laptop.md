---
title: "How to let Ubuntu know that the PC is a Laptop?"
date: 2018-08-02
forum: Hardware
---

### Post by m1nicrusher on 2018-08-02
Recently, I made a desktop-based laptop.(A laptop-shaped PC with desktop motherboard, CPU, memory and GPU)
I'm thinking of adding a battery for it and I'm wondering that how Ubuntu detects my battery like showing battery percentage at the upper right corner.
At least, when I type "sudo dmidecode --string chassis-type", how to let it replys "Laptop"?

So how to let Ubuntu think that my computer is a laptop?
**Help me plz...**

---

### Post by Yellow Pasque on 2018-08-03
> When I type "sudo dmidecode --string chassis-type", how to let it reply "Laptop"?

dmidecode is reading the motherboard's SMBIOS table. You cannot change this without custom BIOS/EFI hacks. Google hard enough and you will probably find tools to do it. If you try it and break/brick your system, you keep the pieces.
I don't think it would accomplish what you want.

> I'm thinking of adding a battery for it and I'm wondering that how Ubuntu detects my battery like showing battery percentage at the upper right corner.

I'm not sure exactly how you are rigging up the battery, but the motherboard would have to be able to query the battery through ACPI. If the mobo fills out /proc/acpi/battery properly, that is half the battle.

---

### Post by mastablasta on 2018-08-06
how long would a battery power the desktop? UPS for example can only do it for a couple of minutes.

---

