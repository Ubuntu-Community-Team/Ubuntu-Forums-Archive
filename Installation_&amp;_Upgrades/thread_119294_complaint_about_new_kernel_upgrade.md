---
title: "complaint about new kernel upgrade"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by wwuster on 2006-01-19
I just upgraded to the new kernel but found out that it erased my settings in /boot/grub/menu.lst. Can the installation script at least make a backup copy of it before overwriting it?

William

---

### Post by nocturn on 2006-01-19
[QUOTE=wwuster]I just upgraded to the new kernel but found out that it erased my settings in /boot/grub/menu.lst. Can the installation script at least make a backup copy of it before overwriting it?

William[/QUOTE]

This happens because it runs grup-update.  I have the same issue (I lock most options in grub).

---

### Post by wwuster on 2006-01-19
Now I added menu.lst to the list of files in my backup script.

---

