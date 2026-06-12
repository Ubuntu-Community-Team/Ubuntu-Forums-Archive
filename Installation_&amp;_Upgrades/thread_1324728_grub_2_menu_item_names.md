---
title: "grub 2 menu item names?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by ShadowMage on 2009-11-12
Hi,

Does anyone know if there is a way to change the names of the items in the bootloader menu of grub 2? If I'm not mistaken, grub legacy showed the version of ubuntu (e.g. 9.04), but my grub 2 bootloader does not display this. Not a huge deal but on one comp I have multiple versions of ubuntu and it would be nice to see this number. For now I distinguish them in the bootloader by the linux kernel version, which is displayed.

I am currently using "GNU GRUB version 1.97~beta4". The ubuntu versions are 9.04 and 9.10.

Thanks.

---

### Post by blandhrr on 2009-11-13
See following:

[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

I found this extremely helpful in accomplishing what you have described.

---

### Post by ShadowMage on 2009-11-14
Thank you, blandhrr! That is a very helpful guide. It was enough to not only accomplish what I described, but to also further customize the menu exactly how I want it.

I would post my solution, but it took quite a bit of tinkering and I don't think I'm able to give a clear explanation. However, if you understand drs305's guide that blandhrr's post above links to, then I can say as a tip that for your **system partition** (i.e. in the *10_linux* file) you can get the string "Ubuntu X.XX" by doing, for example:
```
  ## User-added variables
  description="`lsb_release -ds`"
  ##
```This detail is not found in the guide. (Great guide though!)

---

