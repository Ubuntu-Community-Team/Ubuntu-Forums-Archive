---
title: "[SOLVED] SUID root not being honored on /sbin/mount.cifs"
date: 2008-11-20
forum: General Help
---

### Post by digitijit on 2008-11-20
I am trying to allow users to mount/unmount smbfs network shares under Ubuntu 8.10.  

As usual, sudo mount.cifs ... works fine.  Both /sbin/mount.cifs and /sbin/mount.smbfs are SUID root.  However, mount attempts from ordinary user privileges fail with the message "...mount error: permission denied or not superuser and mount.cifs not installed SUID."

Any ideas about why SUID root on /sbin/mount.cifs is apparently being ignored?

Thanks!

---

### Post by bodhi.zazen on 2008-11-20
I do not have an answer to your question, just a "work around".

I just give users sudo w/o a password to mount cifs shares (sudo visudo)

---

### Post by digitijit on 2008-11-29
That will do.  Thanks bodhi.zazen!!!!

---

