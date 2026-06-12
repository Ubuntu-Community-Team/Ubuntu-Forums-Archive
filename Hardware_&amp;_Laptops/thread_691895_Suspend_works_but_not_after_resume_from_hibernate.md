---
title: "Suspend works but not after resume from hibernate"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by tarmack on 2008-02-09
I have the strangest problem here on an old Satellite Pro 4200, Suspend works great, always did exept for some modules and network troubles wich were no problem resolving.
Last night I upgraded to the Hardy repos (from Feisty) after this everything still works great, even hibernation works now, this was the pleasant surprise.
But now the less pleasant surprise: if I do a hibernate, the system does what its supposed to do, it hibernates and recovers great. The problem comes after that, if I now close the lid and the system goes into suspend (wich works) it seems to do every thing needed, but when I then try to resume, the BOIS warn's me about an unsuccesfull resume.

Inspecting the syslog gives me a little clue, the system seems to never have started the suspend scripts, it only turned the system in suspend but it seems the memory is not saved in the right state or the BIOS doesn't know were to start of.

From here on my knowlege of the powermanagement is stuck.

BTW. I use a custom 2.6.23 kernel because the stock kernels don't work good with the ACPI from this BIOS (they slow down the CPU with quite execive C-state changes).

Any help would be very great, I'l now continue my yahoo searches.

---

### Post by tarmack on 2008-02-13
OK an update:
The problem seems to be solved, I don't know exactly why but I think building a 2.6.24.2 kernel might had something to do with it.

Anyway It all works now, hibernate and after that suspend doesn't crash my system now.

---

