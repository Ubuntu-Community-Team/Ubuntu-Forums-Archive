---
title: "reinstall 8.10 upgrade"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by evrkusd on 2009-02-01
hi,
is there a way to basically reinstall the main components of an 8.10 upgrade? 
since i've upgraded there have been some issues with my boot process... (it hangs on certain entries until i hit return to prompt it to continue)
i'm fairly certain this is a result of me choosing to not replace or merge or replace etc. certain files during the upgrade. I'm assuming it would be better to just go back and reuprade if that is possible and just replace the files...

any way to do somethign like this (or just fix the boot issue?)

thanks a lot

---

### Post by tuxxy on 2009-02-01
Move your /home to its own partition first to save any important files/settings you have, once done you can install 8.10 from CD and at the partitioning stage select your / partition to install to and assign it the mountpoint of / also be sure to give your new /home partition a mount point /home from the drop down menu.

Now you will install a new filesystem over your old one without deleting your /home

---

### Post by evrkusd on 2009-02-01
there isn't a way to just reinstall key components of 8.10 via the package manager?

---

