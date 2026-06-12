---
title: "GParted Failure"
date: 2008-11-29
forum: General Help
---

### Post by sargonious on 2008-11-29
I recently decided to rid myself of Ubuntu after a not so stellar install of the new Kubuntu and now I find myself with a damaged mbr. Where do I go from here? I just want to delete GRUB. What to do?

---

### Post by oilchangeguy on 2008-11-29
> **sargonious said:**
> I recently decided to rid myself of Ubuntu after a not so stellar install of the new Kubuntu and now I find myself with a damaged mbr. Where do I go from here? I just want to delete GRUB. What to do?

ok, what have you done? have you removed the ubuntu partition? more details would be helpful. and restore the mbr of what, windows? no one here is a mind reader (i think) so you have to give details.

---

### Post by caljohnsmith on 2008-11-29
Since you want to get rid of Grub, I assume you want to replace it with a Windows MBR? If that is the case, just boot your Windows XP Install CD, go to the "recovery console" and run:
```
fixmbr
```
Or if you have a Vista Install CD, it would be:
```
bootrec /fixmbr
```
If you don't have either of those CDs, then if you boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Red"]sda[/COLOR]
```
And replace "sda" with the drive in question, that will write a Windows MBR to the drive. How about giving one of those methods a try and let me know how it goes.

---

