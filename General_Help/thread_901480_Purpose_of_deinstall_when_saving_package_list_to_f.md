---
title: "Purpose of deinstall when saving package list to file"
date: 2008-08-26
forum: General Help
---

### Post by sofasurfer on 2008-08-26
I have found this command to work best for my purpose of saving a copy of my package list to a file for later reinstallation of all packages...

dpkg –get-selections | grep -v deinstall > /media/backup/package-list 

But I can not figure out what role the "deinstall" plays in the process. I am not installing or deinstalling anything at this time.

Please explain.

---

### Post by sofasurfer on 2008-08-28
Bump?

---

