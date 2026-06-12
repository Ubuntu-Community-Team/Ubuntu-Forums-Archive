---
title: "Edgy Memory troubles (slow performances, Sound)"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by pgiacomo69 on 2007-01-10
Installed Ubuntu Edgy on a partition om my Asus M3N Laptop:

Centrino 1,6 GHz
1 GB Ram
80 GB Hd
Ubuntu Partition: 15 GB
Swap Partition: 2 GB
Intel Centrino Chipset Video card with shared memory
Intel Chipset Sound Card (seen by windows as "Sigmatel audio")

Installation process went very slow, after installed Ubunt itself runned veeeery slowly.
I've tried multiple solution from this forum (acpi=off, noapic, no ipv6, etc.) but none worked. Guessing a memory trouble, I removed a 512MB simm to see what happens, rebooted, then MIRACLE, very fast booting, very fast running (also gnome with compiz).
After this, I plugged again the 512MB simm, and appended 'mem=512m' at kernel arguments, rebooted, system was again fast, but.... the  souncard is not detected. I tryed many workarounds to this problem, but, actually the only solution that works, is to remove the 512MB simm again.

Does anyone know of this problem?
Thanks

---

### Post by Jussi Kukkonen on 2007-01-10
Sorry, no help here. Just thought to remind you of the bug database since it's clearly a bug: 
whether or not you find the help here, please report the bug in launchpad too -- that way the relevant developers will hear about it.

[https://bugs.launchpad.net/bugs/bugs/+package](https://bugs.launchpad.net/bugs/bugs/+package)

---

### Post by pgiacomo69 on 2007-01-10
Yesss, I know if it can be a bug, followwing your hint I postedthe description on the bug dtatabase. 
But I would appreciate if anyone can help me to get around .
Thanks

---

