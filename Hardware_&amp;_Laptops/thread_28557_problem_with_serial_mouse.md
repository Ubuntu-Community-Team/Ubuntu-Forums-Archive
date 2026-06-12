---
title: "problem with serial mouse"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by javi7v on 2005-04-20
it does not work my serial mouse. I've done a base installation for a P100 w/ 64MB

i've changed the /etc/X11/xorg.conf file setting the mouse with /dev/ttSO
protocol is 'auto'

i dont know what's wrong, can anybody help me?

thxs

---

### Post by nad on 2005-04-20
That should be /dev/ttyS0. That is a zero at the end.

Dan M

---

