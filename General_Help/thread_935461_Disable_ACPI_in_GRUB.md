---
title: "Disable ACPI in GRUB"
date: 2008-10-01
forum: General Help
---

### Post by phil128 on 2008-10-01
Hi all! I'm trying to disable ACPI from being used on my laptop as it really screws up my system BIG time! I know its ACPI thts screwing my system as i disabled this in other distro's. This is the only Distro that i'm using tht uses GRUB, i've always used LILO and i know how to use tht but GRUB is bloody weird to me!

Could somebody tell me how to disable ACPI in grub please?

Please be easy on me as i don't know how to use GRUB.

Thanks people

---

### Post by phidia on 2008-10-01
If you open /boot/grub/menu.lst with "gksudo gedit" (that's an editor with root permission) you can add "acpi=off" to the line that lists your ubuntu install.

Look for the line in menu.lst that says > ## ## End Default Options ##
right after that you should see the line for your install.

---

