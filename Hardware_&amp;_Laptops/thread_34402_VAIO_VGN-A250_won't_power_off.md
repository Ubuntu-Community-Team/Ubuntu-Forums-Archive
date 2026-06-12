---
title: "VAIO VGN-A250 won't power off"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by MonkeyWrench32 on 2005-05-14
When I go to shut down Ubuntu, it does the normal routine, then the screen goes black but my VAIO does not physically shut off (I have to hold down the power button for a few seconds).  It shut down on its own when I had Fedora Bloatcore 3 on here.

Any suggestions?

---

### Post by MonkeyWrench32 on 2005-05-14
Fixed it!  I just had to add "nolapic" to the kernel line in menu.lst.  :)

---

