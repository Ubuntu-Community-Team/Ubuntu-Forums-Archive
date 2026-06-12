---
title: "Synaptic Package Manager will not run"
date: 2008-10-07
forum: General Help
---

### Post by specrdr9 on 2008-10-07
When I try to open the Synaptic Package manager it gives me an error saying E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


when I try to run dpkg --configure -a it tells me i need superuser privelages...

Help...?

---

### Post by christianvaldes on 2008-10-07
run 
sudo dpkg --configure -a

---

### Post by specrdr9 on 2008-10-07
thank you

---

