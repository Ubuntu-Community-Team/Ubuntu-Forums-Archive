---
title: "Display Problem"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Malviolent on 2007-09-03
I'm running Ubuntu 6.10 with a 20.1" Sceptre (1680x1050 preferred resolution) with an nvidia GeForce 6600.  On windows I can properly run the maximum resolution at 1680x1050; however, with unbuntu my monitor receives an "Out of Range" error whenever I try to bump my resolution higher than 1440x1024.  The vertical refresh and horizontal sync rates are all within what my monitor requires (43.0 - 60.0 and 28.0 - 72.0 respectively).  I'm using the latest nvidia driver, and not nv.  Thanks for all the help!

---

### Post by Malviolent on 2007-09-09
bump, can anyone help?

---

### Post by glotz on 2007-09-09
How about```
sudo dpkg-reconfigure xserver-xorg
```
followed by <ctrl>+<alt>+<backspace> to restart X.

---

### Post by Malviolent on 2007-09-10
I've reconfigured my xorg so many times already, and every time I try to use any resolution higher than 1440x900 (even the native resolution) I get an out of range.

---

