---
title: "Asus P4P800+P4 : SMP and ACPI troubles..."
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by gerard lambert on 2007-04-27
Hi,
I have a P4P800 Deluxe motherboard and a P4 3.0 Ghz.
I recently installed Ubuntu Feisty and it works really well.
However I have some problems :

- SMP does not recognize HyperThreading on my processor and I get the following message at startup  :
"SMP mptables : no processor registered!". Then SMP is disabled. I have Hyperthreading activated in the bios and it works well under WinXP.

- I have to disable ACPI (otherwise Ubuntu won't boot) so I can't use the Hibernate mode (my computer freezes), and when I shutdown Ubuntu I have to press the power button to turn my computer off.

Maybe my motherboard is not supported? :confused:  Or maybe I have to set some values in the BIOS?
Any idea is welcomed :guitar: 
Thank you very much and long live to Ubuntu

---

### Post by gerard lambert on 2007-04-28
Anyone?

---

### Post by djtexho on 2008-01-29
Gerard, ACPI is required to initialize hyperthreading. Try booting your kernel with option appended (via GRUB menu or edit /boot/grub/menu.lst):

[FONT="Courier New"]acpi=ht[/FONT]

This will briefly enable ACPI during boot-time to initialize hyperthreading, and will disable it afterwards.

---

