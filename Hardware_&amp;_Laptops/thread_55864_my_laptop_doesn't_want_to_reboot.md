---
title: "my laptop doesn't want to reboot"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by earendilion on 2005-08-10
Hey all,

I've a little problem with my laptop (HP nx6110). I installed ubuntu custom version, and kde 3.4, then uninstalled gnome.
My problem is, when I try to reboot the whole system, it stops with the line "Restarting the system" or something like that...and a blinking cursor below.
To put an end to this I must push the powerbutton of the laptop, something I think he doesn't really appreciate...
I thought it was acpi which made that, but after disabling all acpi options it continues...
You'll note that when I run "Halt" in terminal, it halts correctly...

Any idea ?

---

### Post by pmjdebruijn on 2005-08-10
Hi,

Have you tried modprobing the apm module?



Well this could also be a BIOS issue... Laptops are notorious for having crappy BIOSses... 
If I'm not mistaken when the kernel tries to reboot your machine it does a jump to a certain fixed position in your systems memory. This position is located inside the BIOS address space... So if this is in some way abbarant, it won't work... So you could maybe try a BIOS update?

Regards,
Pascal de Bruijn

---

### Post by earendilion on 2005-08-10
Problem solved: I added the "reboot=b" to the kernel line of /boot/grub/menu.lst.
I discovered it's a specific problem of the HP nx* series with Ubuntu.
Thank yu for your help  :)

---

