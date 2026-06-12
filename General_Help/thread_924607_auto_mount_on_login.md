---
title: "auto mount on login"
date: 2008-09-19
forum: General Help
---

### Post by dhysk on 2008-09-19
I would like to auto mount my windows partition when I log in as a specific user.  I don't want to mount on start up because, unless im mistaken, all users could see it then i would have to deal with permissions and all that.  Is there a way to do this or do i just have to mess around with fstab and all that?

---

### Post by aysiu on 2008-09-20
It's possible it might work, but I can't test it.

If you add a line like this to your /etc/fstab file, it might work: ```
/dev/hda1 /mnt/ntfs ntfs-3g uid=1000,umask=077 0 0
``` if your user is uid 1000.

---

