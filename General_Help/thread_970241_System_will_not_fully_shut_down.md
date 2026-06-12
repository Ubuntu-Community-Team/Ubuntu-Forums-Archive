---
title: "System will not fully shut down"
date: 2008-11-04
forum: General Help
---

### Post by hot dog on 2008-11-04
Does anyone know how to add:

**acpi=force**  to the Ubuntu configuration?

I've done it before, I just can't remember how to do it.  When I shutdown my computer it stops shuting down after a certain point and just hangs there, with a Ubuntu logo displayed.  When I added  acpi=force  it fixed the problem before, but like I said, I just can't remember how to do it.:confused:

thanks

---

### Post by sahabcse on 2008-11-04
To add 'acpi=force' to the line in /boot/grub/menu.lst beginning '# defoptions='. Then (as root) run: 

Regards
Sahab

---

