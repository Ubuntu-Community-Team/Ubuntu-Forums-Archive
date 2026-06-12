---
title: "No permission in var/www"
date: 2008-11-17
forum: General Help
---

### Post by Dawinci on 2008-11-17
probably an issue that has been evident a few times ...

But wonder how I can create / modify / delete files in the folder var / www

Right now i dont have permission to do that...

---

### Post by Marius Derekus on 2008-11-17
Use the ```
gksudo nautilus
``` command. It will give you a seperate window that has all the permissions you need (you can even change the permissions through that window so that any window will have super permissions, although many would not advise it)

---

