---
title: "reinstallation of Windows &amp; Ubuntu installation"
date: 2008-10-04
forum: General Help
---

### Post by Okeefe on 2008-10-04
hi!

I have two Questions where I couldn't find an answer in the FAQ:

If I want to reinstall Windows XP, is it enought to just install wubi on the new System again and copy the partition-file to the same place to get the old Ubuntu installation back?

Is the Wubi-Ubuntu-Installation completely the same as the normal Ubuntu (same possibilities to change settings while installing, etc.)?

thx!

---

### Post by ago on 2008-10-06
> **Okeefe said:**
> 
If I want to reinstall Windows XP, is it enought to just install wubi on the new System again and copy the partition-file to the same place to get the old Ubuntu installation back?
Yes, you need to copy back root.disk and the /boo folder, note that if you reformat, you might have to edit /boot/grub/menu.lst as the UUID of your partition might change.

> Is the Wubi-Ubuntu-Installation completely the same as the normal Ubuntu (same possibilities to change settings while installing, etc.)?
Wubi uses the same ubuntu installer, but most questions are not asked at all. You can still fiddle with the details by manually editing the preseed.cfg file before rebooting.

---

