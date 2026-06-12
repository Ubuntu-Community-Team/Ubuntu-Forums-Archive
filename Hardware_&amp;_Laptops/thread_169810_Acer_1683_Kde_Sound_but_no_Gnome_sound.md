---
title: "Acer 1683 Kde Sound but no Gnome sound"
date: 2006-05-03
forum: Hardware &amp; Laptops
---

### Post by swebb99 on 2006-05-03
Hi there,

My laptop plays sound fine when I run up using KDE but when I run Gnome I hear some sound as it boots up but thats it. Any idea's ?

Thanks

Steve

---

### Post by Sef on 2006-05-03
Copy and post these the result of these two commands below.


cat /proc/asound/cards

sudo gedit /etc/modprobe.d/alsa-base

---

