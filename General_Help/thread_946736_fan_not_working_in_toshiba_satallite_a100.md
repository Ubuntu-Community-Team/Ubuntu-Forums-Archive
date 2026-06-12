---
title: "fan not working in toshiba satallite a100"
date: 2008-10-13
forum: General Help
---

### Post by terry_gardener on 2008-10-13
i have filed a bug for my fan not working in intrepid and i have been told to add patches and also boot option acpi.power_nocheck=1 

i have done searches and i have finally found out how to do the boot option section. 

when i added the acpi.power_nocheck=1 to menu.lst saved it and then ran sudo update-grub and then rebooted ij get message message unknown boot option acpi.power_nocheck=1 ignoring. 

any ideas. 

Thanks 

[http://bugzilla.kernel.org/show_bug.cgi?id=11691](http://bugzilla.kernel.org/show_bug.cgi?id=11691)
[http://ubuntuforums.org/showthread.php?t=749456](http://ubuntuforums.org/showthread.php?t=749456)

---

### Post by Marvin on 2009-02-10
The acpi.power_nocheck patch has only recently been added to the intrepid kernel.
For hardy the fix is only available in hardy-proposed at this time.

---

### Post by terry_gardener on 2009-02-22
thank you marvin.

---

