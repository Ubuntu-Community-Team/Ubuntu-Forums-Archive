---
title: "Partition Icon"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by madcow on 2006-04-21
Hy "Ubuntoers",sorry for my poor English,
after few ours spent with trying to write on ntfs partition , finally I reached!
Now Ubuntu automatically mounts the ntfs partition R/W, but it doesn't create the icon on the Desktop, and I have to access this browsing via Nautilus...what can I do? thanks!!!:) :) :) :) :)

---

### Post by z_diver on 2006-04-21
[QUOTE=madcow]Hy "Ubuntoers",sorry for my poor English,
after few ours spent with trying to write on ntfs partition , finally I reached!
Now Ubuntu automatically mounts the ntfs partition R/W, but it doesn't create the icon on the Desktop, and I have to access this browsing via Nautilus...what can I do? thanks!!!:) :) :) :) :)[/QUOTE]
Press Alt+F2 and type gconf-editor.  Browse to [COLOR="Red"]system/storage/display_internal_hard_drives[/COLOR] and check the box.  

That should make your internal drives be displayed on the desktop.

---

### Post by madcow on 2006-04-22
I can't find that key...maybe cause I'm using Dapper...:confused:

---

