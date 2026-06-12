---
title: "Ubuntu/Debian boot."
date: 2020-04-23
forum: Hardware
---

### Post by rubberduck1968 on 2020-04-23
I'm wondering if it's possible to run a second hard drive which already has Debian 9 installed on it next to my Ubuntu 20.04 hard drive in my PC. How would you go about setting up the dual boot between the two systems?

Cheers.

---

### Post by CelticWarrior on 2020-04-23
If all OSes are installed in the same mode, i.e., BIOS or UEFI, it should be easy. Just run 'sudo update-grub' from the main system - it should detect the other one and add it to the Grub menu - and then disable os-prober in the second to avoid it hijacking Grub (applicable to old BIOS/MBR installation only).

---

### Post by rubberduck1968 on 2020-04-23
Thank you.

---

