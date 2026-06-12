---
title: "Recover Wrecked Wubi Install"
date: 2008-11-12
forum: General Help
---

### Post by loffing4 on 2008-11-12
User A logged into Ubuntu and accidentally (read: stupidly) moved the /boot and /dev directories to the Windows desktop which was mounted to /media/windows.  User B logged into Windows, didn't recognize these strange directories, and promptly deleted them (and emptied the Recycle Bin).

Now it is impossible to boot Ubuntu.  It fails with an error message indicating menu.lst cannot be found.

Is there a way to repair this install?  Some info in /home is badly needed.  All related info I've found discusses a traditional Ubuntu install with a separate partition, which is obviously not the case with this Wubi install.

Thanks.

---

### Post by Aistina on 2008-11-12
The Wubi wiki mentions two apps that can mount the virtual disks under Windows, perhaps you can recover the files you need so badly using those.

[https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?](https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?)

---

### Post by loffing4 on 2008-11-12
Thanks.  I suppose a little research would have turned that up, sorry.

Now at least files can be retrieved from the Ubuntu install, but is there a way to fix it?  Some way to restore the boot directory?

---

