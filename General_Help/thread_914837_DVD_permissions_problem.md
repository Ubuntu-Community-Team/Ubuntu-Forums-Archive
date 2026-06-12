---
title: "DVD permissions problem"
date: 2008-09-09
forum: General Help
---

### Post by fjf on 2008-09-09
Hi.  My DVD SATA writer seems to work and mounts fine.  However, all of a sudden (without changing anything), when I launch nerolinux it reports no access to /dev/sg1, and burns coasters unless I do sudo chown -R me:me /dev/sg1.  However, the effect is lost when I reboot and I have to do the chown again.  How can I make this permanent?.

Thanks!

---

### Post by anotherdisciple on 2008-09-09
Have you tried going to (System > Administration > Users and Groups)?

Choose yourself and click "Properties"... under the "User Privileges" tab make sure "Use CD-ROM Drives" is checked.

---

### Post by fjf on 2008-09-09
It is checked.

---

### Post by anotherdisciple on 2008-09-09
Edit /etc/group and make sure your username is next to the "cdrom" group.

> sudo gedit /etc/group

---

### Post by fjf on 2008-09-09
It is.

---

### Post by anotherdisciple on 2008-09-09
Wow! I'm fresh out of advice... this is a cheesy way to do it, but you could go to (System > Preferences > Sessions) and try adding the command:

```
gksudo chown -R me:me /dev/sg1
```

it should ask you for you password every time you sign in... and it would give you permissions.

There has to be a better way though... I'll keep researching it.

---

### Post by fjf on 2008-09-09
Hey, thanks anyway!.  I'll keep too!.

---

