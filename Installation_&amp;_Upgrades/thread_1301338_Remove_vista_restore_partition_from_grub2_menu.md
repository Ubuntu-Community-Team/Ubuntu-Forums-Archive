---
title: "Remove vista restore partition from grub2 menu"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by walter_j on 2009-10-25
Running kubuntu and ubuntu 9.10. Vista is on sda1, and linux partitions on sdb1. The vista hdd has a recovery partition which i don't want to see when booting. How can i do this? it certainly isn't easy with grub2. Is there a gui for editing grub2 menus?

i've attached a script i found in a forum that added vista to the grub2 menu. it's greek to me (maybe geek).

Walter

---

### Post by Mark Phelps on 2009-10-26
> **walter_j said:**
> ... The vista hdd has a recovery partition which i don't want to see when booting. How can i do this? it certainly isn't easy with grub2. 

That's certainly true -- GRUB2, with all of its scripting, is going to be a LOT HARDER for folks to customize than was legacy GRUB with its simple text file.

>  Is there a gui for editing grub2 menus?
NO -- by design.  GRUB2 developers don't want you editing menu files.

You can read through the Wiki GRUB2 link below: [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by walter_j on 2009-10-26
I ran the following: 

sudo chmod +w /boot/grub/grub.cfg  # Remove 'read-only', necessary even for "root"

sudo kate /boot/grub/grub.cfg 

I deleted the unwanted entries, saved the file, and now the boots are the way i want em.

If i need to rebuild the menus,

sudo update-grub

Maybe there's and approved way of doing it, but this is a quick and dirty way to do it. I'm not sure how to recover if a mistake is made though.

Walter

walter

---

### Post by jimbo99 on 2009-10-27
Grub from menu.lst to grub.cfg.  Shouldn't they have complied with standards and called it grub.conf?

---

