---
title: "OS installed into pendrive, blocks bios on some reboots, faulty shutdown?"
date: 2012-02-09
forum: Hardware
---

### Post by parix on 2012-02-09
I have Ubuntu 11.10 installed into a Kingston DatatTraveller G3 (PMAP), 16GB, that on some reboots, halts the BIOS, and doesn't boot:

[EDIT]: If a reboot directly there's no problem, but **if I power off, then on** with the computer's power button then** the problem arrives. **

Grub is installed into the pen-drive, but when it happens it doesn't even load GRUB because it is the BIOS that is halted by the pen-drive. If I remove the pen-drive the boot process continues as normal, and if i plug it before BIOS can read the internal HDD boot, it halts again.

Powering off the computer or unplugging the pen-drive don't solve the problem.

But i have a way to "reset" the pen-drive: just plugging it into a computer running windows. So i guess it is something related with Ubuntu not "ejecting" the pen-drive properly when shutting down. Any ideas/suggestions? Thanks!

(the computer is a PB Dot S, bios v.1.16, cpu n270)

---

