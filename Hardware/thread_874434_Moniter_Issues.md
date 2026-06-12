---
title: "Moniter Issues"
date: 2008-07-29
forum: Hardware
---

### Post by 42reasons on 2008-07-29
****Monitor goes into power saving mode as soon as i log in... can this be changed using grub> scripts?

---

### Post by ModelM on 2008-07-30
I think what is probably happening is that the settings for X don't match your monitor, so it shuts off to protect itself.

Post here the contents of the file:

/etc/X11/xorg.conf

and we can have a look...

---

