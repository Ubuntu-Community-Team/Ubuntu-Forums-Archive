---
title: "[SOLVED] no logo"
date: 2008-11-22
forum: General Help
---

### Post by Rita G. on 2008-11-22
anybody know how to boot in text mode?

(so i don't have to see that obnoxious logo)

---

### Post by marshall.robert on 2008-11-22
install startup manager from Add/Remove...

---

### Post by PocketDog on 2008-11-22
```
 gksudo gedit /boot/grub/menu.lst
``` from Terminal. (backup menu.lst first) Remove 'splash' from the end of the kernel line you're using. Save and reboot

---

### Post by Rita G. on 2008-11-22
i thank both of you sweeties!

just learned 2 new things!

---

