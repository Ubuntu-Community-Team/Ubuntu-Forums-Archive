---
title: "Eliminating Windows XP forever"
date: 2008-07-16
forum: General Help
---

### Post by Uchiha_madara on 2008-07-16
Hi Every one , Since I Installed Ubuntu , i never use WinXp


>  -- can I remove WinXp  From it's [NTFS Drive "C:" and from GRUB] Or Not??

> if The Answer is Yes ..... How ???:popcorn:

---

### Post by logos34 on 2008-07-16
gksudo gedit /etc/fstab

remove windows entry (if applicable)

gksudo gedit /boot/grub/menu.lst

remove windows stanza at bottom

Reboot from the ubuntu live cd

>system>admin>partition editor

delete windows partition

grow ubuntu to take up the empty space (slow), or just format it ext3 and use it as data partition or whatever

reboot and [add fstab entry]("http://www.psychocats.net/ubuntu/mountlinux") if you did the latter

---

### Post by Sef on 2008-07-16
Also when you reinstall Ubuntu, you could partition the entire disk.

---

### Post by Uchiha_madara on 2008-07-16
thanks a lot:popcorn:

---

