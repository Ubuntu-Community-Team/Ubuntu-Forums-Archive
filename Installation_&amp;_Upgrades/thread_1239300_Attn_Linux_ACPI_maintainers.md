---
title: "Attn: Linux ACPI maintainers"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Lord Grover on 2009-08-13
Attempting install 9.04 on Dell Optiplex 755, BIOS v 2.2.2

```
[   23.237292] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI_PS
 objects in a way that Linux understands. Please reports this to the Linux ACPI
aintainers and complain to your BIOS vendor.
[   23.237292] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI_PS
 objects in a way that Linux understands. Please reports this to the Linux ACPI
aintainers and complain to your BIOS vendor.
Loading, please wait...

BusyBox v1.10.0 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Have updated to latest Dell BIOS, enabled and disabled cool 'n' quiet, tried no ACPI switch - to no avail. Any ideas people?

---

### Post by ronaldprettyman on 2009-08-13
> **Lord Grover said:**
> Attempting install 9.04 on Dell Optiplex 755, BIOS v 2.2.2

```
[   23.237292] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI_PS
 objects in a way that Linux understands. Please reports this to the Linux ACPI
aintainers and complain to your BIOS vendor.
[   23.237292] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI_PS
 objects in a way that Linux understands. Please reports this to the Linux ACPI
aintainers and complain to your BIOS vendor.
Loading, please wait...

BusyBox v1.10.0 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Have updated to latest Dell BIOS, enabled and disabled cool 'n' quiet, tried no ACPI switch - to no avail. Any ideas people?
Wrong place for this. I'm pretty sure the ACPI devs aren't reading this. But they might....

Try noacpi in your grub
Turn off acpi in your bios

for the grub hit e edit the line for the kernel after splash=what ever and silent all that jazz add
noacpi
enter
b(for boot)
also try noacpi and nomsi
linux kernel ....................... silent noacpi nomsi

---

### Post by Lord Grover on 2009-08-13
As above I tired the noacpi switch via F6 options. There's no ACPI option in the BIOS but I gather the cool 'n' quiet is related so have tried that too. Still no joy.

Any idea where it should be posted then? Can't see anywhere obvious...

---

### Post by ronaldprettyman on 2009-08-13
> **Lord Grover said:**
> As above I tired the noacpi switch via F6 options. There's no ACPI option in the BIOS but I gather the cool 'n' quiet is related so have tried that too. Still no joy.

Any idea where it should be posted then? Can't see anywhere obvious...

Look closer in the bios its their.

I got Debian 4 to install on this system with lilo using the options
nomsi and noacpi
it was a pain, but debian 4 was the only one i had luck with, I was able to upgrade to debian 5 on it, so I'd assume it will run debian 5. I don't have any of these right now though.

But it will run on the Optiplex 755.

---

### Post by Lord Grover on 2009-08-13
> **ronaldprettyman said:**
> Look closer in the bios its their.


It isn't - I promise you. Unless it's called something else but I've just gone through every darn page and there is no reference to ACPI anywhere.

---

