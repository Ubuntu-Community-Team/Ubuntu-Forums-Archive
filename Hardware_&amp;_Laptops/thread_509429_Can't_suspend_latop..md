---
title: "Can't suspend latop."
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by Asako24 on 2007-07-25
For some reason I get prompted for a password when I try to suspend my laptop now.  I tried putting in my regular account password and then it says I'm not authorized to suspend the system.  Does anybody know how to fix this or disable it?

Thanks.

---

### Post by aysiu on 2007-07-25
Try Alt-F2 ```
gconf-editor
``` Apps > gnome-power-manager > lock_on_suspend and unchecking the box.

---

