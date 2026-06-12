---
title: "pcie_aspm=force not working"
date: 2012-03-21
forum: Hardware
---

### Post by JohnDoe365 on 2012-03-21
I experience the terrible power regression in Ubuntu 11.10. I hoped that the 
[FONT=monospace]
[/FONT]pcie_aspm=force

kernel parameter would help me, but no. Thermal issues and battery life is at 50%.

This is my dmesg | grep ASPM output:

[    0.000000] PCIe ASPM is forcedly enabled
[    0.491035] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    1.637943] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.641265] ACPI _OSC control for PCIe not granted, disabling ASPM

Any idea why ASPM is disabled while I force it to on?

3.0.0-17-generic, Intel Sandybridge, Dell E6410

Greetings, Johann

---

### Post by mexicanseaf00d on 2012-06-18
late reply, but anyway:
have you added it to the right spot in grub?

see this askubuntu answer
[http://askubuntu.com/a/68383/3962](http://askubuntu.com/a/68383/3962)

---

### Post by Redblade20XX on 2012-06-18
OP's BIOS table doesn't support aspm so there isn't a reference table for the parameter to use. Maybe a BIOs update will solve it.

-Red

---

