---
title: "No /dev/cdrom after Hoary upgrade from Warty"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by wernst on 2005-03-22
OK, so my Xine won't play DVDs after the upgrade. It turns out that there's no longer my symlink from /dev/cdrom to /dev/dvd becasue THERE IS NO /dev/cdrom anymore after the upgrade to Hoary.

Can someone confirm this for me, or tell me how to create /dev/cdrom that works?

Thanks,
Warr

---

### Post by wernst on 2005-03-22
Answered my own question.

I made a symlink from /dev/hdb to /dev/cdrom and also to /dev/dvd.

Now various things work fine again...

-Warr

---

### Post by out of the blue on 2005-03-26
[QUOTE=wernst]Answered my own question.

I made a symlink from /dev/hdb to /dev/cdrom and also to /dev/dvd.

Now various things work fine again...

-Warr[/QUOTE]
 Is the symlink restored when you restart?

---

