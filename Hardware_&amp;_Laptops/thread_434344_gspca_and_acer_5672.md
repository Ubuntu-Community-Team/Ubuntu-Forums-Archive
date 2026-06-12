---
title: "gspca and acer 5672"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by maxguzenski on 2007-05-05
Hi,
I have a bug in feisty fawn with all updates.

When I boot it shows "Failed to configure camera" and a error in gspcav1... and this error repeat infinitely!

any knows how I disable camera or how I can fix this bug ?

---

### Post by maxguzenski on 2007-05-06
solved:

open blacklist file:
nano -w /etc/modprobe.d/blacklis

and add:
blacklist gspca

---

