---
title: "Boot loader problems"
date: 2008-08-12
forum: General Help
---

### Post by Grykee on 2008-08-12
I recently installed opensuse 11.0 to go with my ubuntu, but for some reason opensuse wouldnt let me boot into ubuntu. In a fit of frustration i installed xp over opensuse. my ubuntu partition is still untouched. So is there a way to add ubuntu to my xp boot menu, or do i have to reinstall ubuntu all over again?

---

### Post by theyranos on 2008-08-12
> **Grykee said:**
> So is there a way to add ubuntu to my xp boot menu

No.
[Quote=Grykee] 
or do i have to reinstall ubuntu all over again?[/QUOTE]
No!

Look [here](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-08-12
> **theyranos said:**
> 
[QUOTE=Grykee;5575818]So is there a way to add ubuntu to my xp boot menu
No.
[/QUOTE]
Actually it is possible to add Ubuntu to the Windows boot loader. You can use [WinGrub]("http://sourceforge.net/projects/grub4dos") (and see [the tutorial at Herman's site on using WinGru]("http://users.bigpond.net.au/hermanzone/p9.html")b) or you can do something similar to [this thread]("http://ubuntuforums.org/showthread.php?t=56723"). Still, I would recommend just reinstalling Grub to the MBR and letting Grub be the boot manager.

---

### Post by theyranos on 2008-08-12
[Quote=caljohnsmith]WinGrub[/Quote]
I learn something new every day. Thanks!

---

