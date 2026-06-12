---
title: "can't delete files."
date: 2008-10-26
forum: General Help
---

### Post by vimalmd on 2008-10-26
I have installed edubuntu. i can delete the files that are in desktop.But i cant delete files in the drives. how can i delete it?

---

### Post by kevstar31 on 2008-10-26
Post your /etc/fstab

---

### Post by vanadium on 2008-10-26
There is no need for you to delete files in places outside of your home directory. If you want to be able to read/write elsewhere, you must first obtain permission from the administrator of the system (that could be yourself!). This is a security model of Ubuntu/linux/unix that works very well: normal users will not be able to destroy the system by accident or willingly.

---

### Post by mikjp on 2008-10-26
> **vanadium said:**
> There is no need for you to delete files in places outside of your home directory. 

Unless you are using an external drive or memory stick that is mounted under /media.

mikko

---

### Post by ghost_ryder35 on 2008-10-26
> **vimalmd said:**
> I have installed edubuntu. i can delete the files that are in desktop.But i cant delete files in the drives. how can i delete it?
sudo

---

### Post by vanadium on 2008-10-27
> Unless you are using an external drive or memory stick that is mounted under /media.
At that point, you are accessing the drive from an icon on your desktop or from the Places menu. There should never be a need for a user to navigate outside his home directory in a system that is setup in a user friendly way.

"sudo" is not an appropriate suggestion, because the user might not have root rights. The only correct answer is: have the administration give permissions to the user to delete files somewhere.

Let the OP explain his purpose. If he needs to delete system files, then let him use sudo. However, then he must be knowing what he is deleting and why.

---

