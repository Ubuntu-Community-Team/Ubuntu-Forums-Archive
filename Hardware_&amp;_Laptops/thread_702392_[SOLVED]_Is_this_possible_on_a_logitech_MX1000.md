---
title: "[SOLVED] Is this possible on a logitech MX1000"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by Kerry_W on 2008-02-20
I'n not even sure if this is possible but figured i'd ask anyway.
I want my left and right scroll wheel functions to be used to copy and paste.

any ideas how i would go about this?
Thanks in advance.
Kerry

---

### Post by Kerry_W on 2008-02-20
never mind.  got it figured out.
just had to edit the.xbindkeysrc file and change to

"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[v]""
  b:13
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[c]""
  b:14


works like a charm.
Kerry

---

