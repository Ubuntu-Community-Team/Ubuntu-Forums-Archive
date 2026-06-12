---
title: "Fans not coming on"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by unconquerable on 2006-08-25
The fans on my hp dv2000t do not come on when the notebook gets hot.  When used on bed or anything else.  It gets very hot to the touch and they come on fine in windows.

Any ideas?

---

### Post by melissawm on 2006-08-25
I don't know if it's the same thing I had, but probably you have to turn on ACPI (it worked for me)

What i did was to edit the /boot/grub/menu.lst , and alter my boot options to include "acpi = on" and "lapic" (these options were disabled because i couldn't install ubuntu if they were enabled):

```
sudo gedit /boot/grub/menu.lst
```

then i searched this line:

```
#defoptions=quiet splash nolapic acpi=off pnpbios=off
```

and edited it to 

```
#defoptions=quiet splash lapic acpi=on pnpbios=off
```

saved the file, rebooted and it worked. I don't know if that could harm your system, but that worked for me...

---

### Post by unconquerable on 2006-08-25
Could not find anything in that file reffering to acpi.


:-k

---

### Post by melissawm on 2006-08-26
Well, did you find the "defoptions" line? Try adding the acpi=on and lapic options there.

---

