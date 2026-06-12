---
title: "[ASK] How to boot into linux using stock VGA driver?"
date: 2010-05-29
forum: Hardware
---

### Post by squiddy on 2010-05-29
Hi, i've got this ATI radeon 3200 HD restricted driver installed, and i want to boot into my box without load the restricted driver. (just want to test the stock driver). what is the safest way to do that?

Thank you.

---

### Post by squiddy on 2010-05-29
bump

---

### Post by bildr on 2010-05-29
make a backup copy of xorg.conf

change in xorg.conf
replace video card driver with vesa

you may have to do something with module also

remember to make a backup

have a rescue CD ready in case you hose something

---

### Post by squiddy on 2010-05-30
thank you for your suggestion

---

