---
title: "[SOLVED] weird, boot cpu (#15) not listed by BIOS"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by NeoFax on 2007-11-17
After running apt upgrade today, I cannot boot my system.  I have tried older kernels than 2.6.22.14 and still receive the problem.  I have tried disabling ACPI as stated on another board to no avail.  I have also tried flashing my BIOS, but that does not work under linux.  Any help would be appreciated.

---

### Post by NeoFax on 2007-11-18
Fixed my own problem.  For some reason the kernel was thinking I had a SMP enabled mainboard(supposedly this is standard on newer kernels).  So, thanks to Minataku's suggestion on IRC, I thought how to fool the kernel into thinking it was a UP system.  I scoured Google and arrived a some Knoppix cheat codes.  I just had to add nosmp to my GRUB menu.lst kernel lines and now it works liked it did a week ago.  Thanks to IRC and Minataku in particular!

---

