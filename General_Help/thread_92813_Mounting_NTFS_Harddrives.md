---
title: "Mounting NTFS Harddrives"
date: 2005-11-20
forum: General Help
---

### Post by etlatino on 2005-11-20
Hello, I am new to linux (newbie).

I have 3 harddrives on my computer, one running linux, one running windows, and one for storage.

Anyway, I have installed Ubuntu and Kubuntu multiply times, playing around with grub and stuff.  Sometimes, Ubuntu will mount my drives automatically and sometimes it doesn't.

At this point I have all my drives mounted on the desktop but when I double click the harddrive it says I don't have permission to access.  But if I clicked system, admin, disk and If i click on each harddrive and click browse, it allows me to browse my files.

Anybody know how I can set the permissions?

etlatino

---

### Post by cylon359 on 2005-11-20
[QUOTE=etlatino]Hello, I am new to linux (newbie).

I have 3 harddrives on my computer, one running linux, one running windows, and one for storage.

Anyway, I have installed Ubuntu and Kubuntu multiply times, playing around with grub and stuff.  Sometimes, Ubuntu will mount my drives automatically and sometimes it doesn't.

At this point I have all my drives mounted on the desktop but when I double click the harddrive it says I don't have permission to access.  But if I clicked system, admin, disk and If i click on each harddrive and click browse, it allows me to browse my files.

Anybody know how I can set the permissions?

etlatino[/QUOTE]

You can edit /etc/fstab and give your windows partitions the option: uid=<your username>

umount and mount, and it should work.

---

### Post by aysiu on 2005-11-20
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

