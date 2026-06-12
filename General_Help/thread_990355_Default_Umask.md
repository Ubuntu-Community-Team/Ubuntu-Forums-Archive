---
title: "Default Umask"
date: 2008-11-22
forum: General Help
---

### Post by tealio on 2008-11-22
I want to set a systemwide default umask.  I read in a debian forum to use libpam-umask, which has apparently been replaced by libpam-modules.  I want to use pam so that no matter how a user is logged in, the umask is always set.  The problem is i don't know how to use the modules, and i don't know where to find documentation. Anyone?

---

### Post by tealio on 2008-11-22
Does no one know, or does no one care?!

---

### Post by Zill on 2008-11-23
/etc/profile script is where the umask command is usually set for all users.

---

### Post by tealio on 2008-11-23
yes, but that doesn't catch every case... it only catches login shells... it doesn't set it for scp, sftp, ftp... there is a pam module for it.  my question is how to set up the pam modules.  it's something i need to know anyway... what i want to use it for is really immaterial.

---

### Post by tealio on 2008-11-25
are the ubuntu forums too good, or too useless to get an answer to a seemingly easy question?  if someone could point me in the direction of some decent documentation i would be satisfied... a real answer as to how to use the modules would be great too, but jesus... all i need is a pointer to documentation...

---

