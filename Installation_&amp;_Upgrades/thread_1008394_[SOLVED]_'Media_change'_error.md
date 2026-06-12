---
title: "[SOLVED] 'Media change' error"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2008-12-11
I'd be very grateful if anyone could help me with this installation problem : halfway through (after partitioning) installing 8.10 from the AMD64 alternate I get a 'Media change' message & am told to insert the CD (which is already inserted). I've tried the boot parameters :

noapic nolapic
acpi=off
irqpoll
lapic pci=routeirq

The only one that has any effect is 'acpi=off', when I get a timeout error for ATA2.00 before reaching the partitioner.

With the Live CD the installation hangs at "Starting Hardware abstraction layer hald".

---

### Post by cariboo on 2008-12-11
I've run into the same problem a couple of times, there is a bug related to this problem, see here:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/270461](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/270461)

The only suggested fix I could find, was to try a drifferent drive.

Jim

---

### Post by pietjanjaap on 2008-12-11
Check your bios.
You can change sata and ide, and maybe a few more settings.(AHCI/ide maybe)

---

### Post by sdbrogan on 2008-12-12
Thanks to both of you !  I couldn't find a BIOS change that helped but it installed fine from CD drive I borrowed from an old PC.  The desktop won't start up but I opened a new thread about that - something to do with HAL & dbus.

---

