---
title: "Toshiba ACPI not enabled in the kernel"
date: 2008-08-07
forum: Hardware
---

### Post by hidinginthemountains on 2008-08-07
I'm back to trying to get the power functions of my laptop (a Toshiba Satellite A-100) working. It has never been able to suspend/hibernate properly with Ubuntu.

I think FnFX is related to this. And it is installed from the Ubuntu repositories. But it can't do anything, because the kernel doesn't appear to have TOSHIBA_ACPI enabled.

```
sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```

I've been doing things with reference to [this page]("http://fnfx.sourceforge.net/index.php?section=doc#kernel.").

Suggestions, comments?

---

### Post by bigbugbg on 2008-08-29
well, it's almost dawn and no success
i have satellite a110 and wanted to use 
more than just bright up/down keys

so far nobody has solved this one
as my impressions suggest...
this module doesn't support/"find"
the "hardware" it's written for

who knows...maybe smb will find and fix it

---

### Post by tvaughn on 2008-11-18
i have a satellite x205 and i cant use fnfx for the same reasons if anyone finds the solution id greatly appreciate it

---

