---
title: "change permissions for more than one file at once"
date: 2008-09-29
forum: General Help
---

### Post by Mzwo on 2008-09-29
hi,

there's probably a rather easy command for this - alas, i'm not aware of it. so: how do i change the read-write-permissions not only for a particular folder, but for all files and folders contained within it? doing so one by one seems a little tedious.

thanks,

Mzwo

---

### Post by Titan8990 on 2008-09-29
You would use the -R flag on the folder:

chmod 775 -R ~/test/

The above command will give 775 permissions to the folder ~/test/ and all children files/directories.

---

