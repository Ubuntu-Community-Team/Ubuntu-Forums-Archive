---
title: "&quot;Toshiba Laptop ACPI Extras version 0.19a-dev&quot; Bug on Satellite Pro 4200"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by gimle on 2007-07-28
I've been trying to get pcmcia to work (at all) on Xubuntu 7.0.4. I've tried a lot of options, but can't get the system to find the cardbus controller. Today i tried a new set of boot options : "pci=conf1 acpi=force" and i set "pci=assign-busses" in /etc/pcmcia/pcmcia.opts. 

After a reboot a bug report appeared in dmesg :

[   62.064000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   62.064000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   62.072000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   62.072000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   62.080000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   62.152000] ACPI: Error installing notify handler
[   62.152000] Device 'dock.0' does not have a release() function, it is broken and must be fixed.
[   62.152000] BUG: at drivers/base/core.c:104 device_release()
[   62.152000]  [<c01ed5f9>] kobject_cleanup+0x49/0x90
[   62.152000]  [<c01ed640>] kobject_release+0x0/0x10
[   62.152000]  [<c01ee2fb>] kref_put+0x2b/0xa0
[   62.152000]  [<c8b95723>] find_dock+0x1d0/0x1f0 [dock]
[   62.152000]  [<c021cb4d>] acpi_ns_walk_namespace+0xf9/0x114
[   62.152000]  [<c021b304>] acpi_walk_namespace+0x57/0x74
[   62.152000]  [<c8b95553>] find_dock+0x0/0x1f0 [dock]
[   62.152000]  [<c883003c>] dock_init+0x3c/0x55 [dock]
[   62.152000]  [<c8b95553>] find_dock+0x0/0x1f0 [dock]
[   62.152000]  [<c014421d>] sys_init_module+0x15d/0x1ba0
[   62.152000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   62.152000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   62.152000]  =======================

So, where to report this ? What can be done?

---

### Post by Cuppa-Chino on 2007-08-11
how did you get it to install? did you use alternate installer cd?

SOLVED - not enough memory to boot live cd

---

