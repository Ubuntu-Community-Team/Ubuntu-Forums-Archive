---
title: "Update manager only does partial update"
date: 2008-10-21
forum: General Help
---

### Post by avanrens on 2008-10-21
I can only do a partial update using update manager,there are many updates but they are grayed out. How do I get it to do a complete update ?

---

### Post by dcstar on 2008-10-21
> **avanrens said:**
> I can only do a partial update using update manager,there are many updates but they are grayed out. How do I get it to do a complete update ?

Updates still in the process of being uploaded to the repository will be cause this - their dependencies have not yet made it to the disks even though the "library" file of the new updates has (why isn't this rsync'ed LAST?, then these things would not occur.......)

Wait a day or two and all should be ok, otherwise your Synaptic is set to install the incorrect available versions.

---

### Post by avanrens on 2008-10-21
It's been like taht for about a week now , but I'll wait and see what happens. Thank you.

---

