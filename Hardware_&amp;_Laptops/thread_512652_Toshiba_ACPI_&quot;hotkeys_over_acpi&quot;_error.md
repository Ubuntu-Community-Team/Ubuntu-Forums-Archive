---
title: "Toshiba ACPI &quot;hotkeys_over_acpi&quot; error"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Neo0351 on 2007-07-29
I've found a few threads all with the same problem and no fix.  I'm running a Toshiba A65-S126 and I've been trying to get to fnfdx or toshset to work.  toshset says that "required kernel toshiba support not enabled."  And fndx says "
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel."

So I went to the website and it said to "modprobe toshiba_acpi" which i get a fatal error
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.22-8-generic/kernel/drivers/acpi/toshiba_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg says: 
toshiba_acpi: Unknown parameter `hotkeys_over_acpi'

Does anyone know how to fix this?  I've even tried to recompile my kernel and that didn't work either.

---

### Post by Neo0351 on 2007-07-31
bump

---

### Post by zxscooby on 2007-08-25
I have the same type of laptop and the same problem.

---

### Post by Ghilteras on 2008-04-11
same issues here.


bug is filed here

[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374)

---

