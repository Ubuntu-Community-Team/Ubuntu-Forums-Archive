---
title: "Can't change file access permissions"
date: 2008-10-08
forum: General Help
---

### Post by leutnant on 2008-10-08
I'm unable to change file access permissions for any folder from "--" to "read and write."

[[IMG]http://img135.imageshack.us/img135/4642/etmainnm0.th.png[/IMG]](http://img135.imageshack.us/my.php?image=etmainnm0.png)[[IMG]http://img135.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Clicking "Apply permissions to Enclosed Files" does nothing because the permissions always revert back to "--"

Please help

btw, I'm aware I have a similar thread in the gaming subforum. I'm sorry for that. The mods can delete it if they want because I just realized that this is problem is not caused by enemy territory but rather, is a problem in and of itself.

---

### Post by Mister.Vash on 2008-10-09
You might not have right to change it if you don't have rights to the original mount point.  Or you might not be able to change it because it isn't owned by you.

For the item that you want to change can you list the full path that it is at.  Also, list the settings from fstab.  For the folder you are having trouble with, post the output of a 'ls -la' command - also post the output of whoami

---

### Post by iaculallad on 2008-10-09
Does those files/foders you're trying to change it's permission reside on an NTFS partition? If so, Linux permission does not apply to NTFS formatted drives/partitions so it always revert back to its original permission when you try to change it.

---

### Post by leutnant on 2008-10-09
Thanks, solved the problem via this thread: [http://ubuntuforums.org/showthread.php?t=942013](http://ubuntuforums.org/showthread.php?t=942013)

:guitar:

---

### Post by leutnant on 2008-10-10
edit: please delete this. Thanks

---

