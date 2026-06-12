---
title: "Going to buy a new monitor..."
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by Neo40 on 2005-12-27
Hi,

I have Ubuntu installed with my old monitor. I'm going to buy a new one soon. Does Ubuntu will detect my new monitor automatically  or do  I have to edit my xorg.conf myself?

Thanks for your help!

---

### Post by Imexius on 2005-12-27
Depends on what type of monitor you buy really. If anything all you would have to change is the screen resolution.

---

### Post by stuporglue on 2005-12-27
[QUOTE=Neo40]Hi,

I have Ubuntu installed with my old monitor. I'm going to buy a new one soon. Does Ubuntu will detect my new monitor automatically  or do  I have to edit my xorg.conf myself?
[/QUOTE]

You won't have to edit your xorg.conf yourself. If the new monitor doesn't "just work", back up the old xorg.conf, then run dpkg-reconfigure xserver-xorg. It will generate a new xorg.conf for you.

---

