---
title: "Have anyone upgraded the kernel to 2.6.27-11?"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Pidgin on 2008-12-20
I have met a mysterious problem. I am using the mirror "mirror.lupaworld.com" located in China, which is among the official approved mirrors and can be selected in Software Sources. Yesterday the mirror released the following packages:
```

linux-headers-2.6.27-11-generic
linux-image-2.6.27-11-generic

```
But it did **[COLOR="Red"]NOT[/COLOR]** provide:
```

linux-restricted-modules-2.6.27-11-generic

```
That resulted in that after upgrading the kernel to 2.6.27-11, I could not use the wireless, which I guess was caused by a lack of corresponding version of linux-restricted-modules. When I booted into the 2.6.27-10 kernel, the wireless worked well.
I have noticed that other official mirrors had not yet released the new kernel. I am not very clear about how to settle the problem.

---

### Post by Sef on 2008-12-20
Yesterday was a partial upgrade.  Today the rest of it was upgraded.

---

### Post by schimschone on 2008-12-21
I also did a forced update yesterday.. accidentally. Today the rest of the package was released, but unfortunately 2.6.27-11 now won't allow my ethernet to work.. so I'm still using 2.6.27-10. You can load it during start up by pressing esc just after your BIOS screen, and if you reedit GRUB you can load it automatically. 

I don't know if it's popular, but it works, and it may be the only way to get internet working for long enough to download the updates.

schim

---

### Post by Pazau on 2008-12-23
I have upgraded to 2.6.27-11 today, and i works properly and fast. :D

---

