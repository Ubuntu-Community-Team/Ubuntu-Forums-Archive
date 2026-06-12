---
title: "Where is trash folder located?"
date: 2008-08-27
forum: General Help
---

### Post by Timberwolf5578 on 2008-08-27
I want to make a desktop shortcut for the trash folder, but I can't find the location of it.  Please help.

Thanks.

---

### Post by iaculallad on 2008-08-27
> **Timberwolf5578 said:**
> I want to make a desktop shortcut for the trash folder, but I can't find the location of it.  Please help.

Thanks.

It's in:

> ~/.local/share/Trash/files

---

### Post by Victormd on 2008-08-27
To add the trashcan to the desktop, you can also open a terminal and type:
```
gconf-editor
```
then go to
> apps>nautilus>desktop
and check "trash_icon_visible"

---

