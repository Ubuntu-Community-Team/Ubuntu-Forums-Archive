---
title: "Graphics"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by Zeek00 on 2006-10-21
Hey,

How does Ubuntu handle changes to graphics cards? Does it autorecognize and configure them? Do I need to do some nasty bloody task to get it configured and working?

Thanks,
Zeek

---

### Post by az on 2006-10-21
> **Zeek00 said:**
> Hey,

How does Ubuntu handle changes to graphics cards? Does it autorecognize and configure them? Do I need to do some nasty bloody task to get it configured and working?

Thanks,
Zeek

It does not autodetect a new card.  You need to boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

the first time you boot the computer with the new card in it.

Then run
init 2 to get out of recovery mode and into the desktop.

---

