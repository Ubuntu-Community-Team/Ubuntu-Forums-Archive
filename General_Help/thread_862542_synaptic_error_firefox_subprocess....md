---
title: "synaptic error firefox subprocess..."
date: 2008-07-17
forum: General Help
---

### Post by chris4585 on 2008-07-17
in synaptic, or update manager i keep getting this error message:
> 
E: firefox-2: subprocess post-installation script returned error exit status 1

any clues?

---

### Post by ajgreeny on 2008-07-17
In the bottom status bar of synaptic, does it say you have any broken packages?  If so use the Edit Menu>>Fix broken packages.  That may do the trick.  If not try completely uninstalling Firefox and then reinstalling it, perhaps even renaming your ~/.mozilla folder temporarlly, just in case there is something in your FF config causing a problem (seems unlikely, but worth trying, I think).

---

### Post by chris4585 on 2008-07-17
Thanks that helped, oddly enough i tried fixing the packages before.

---

