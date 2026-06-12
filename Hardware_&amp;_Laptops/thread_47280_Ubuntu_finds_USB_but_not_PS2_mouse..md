---
title: "Ubuntu finds USB but not PS2 mouse."
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by allforcarrie on 2005-07-08
What is the deal? how can I get my PS2 mouse detected?

---

### Post by Yagisan on 2005-07-09
check /etc/modules and see if you have two lines that read
mousedev
psmouse

If not, add them both in that order to the end of the file. If you only have one, add the missing line, with mousedev being listed before psmouse. Reboot, and all should be fine.
Technically you could just run```
modprobe mousedev && modprobe psmouse
``` but if you don't edit /etc/modules they won't be loaded on startup.

---

### Post by allforcarrie on 2005-07-09
thanks, I'll check it out.

---

