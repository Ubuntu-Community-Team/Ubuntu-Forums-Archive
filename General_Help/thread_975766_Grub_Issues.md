---
title: "Grub Issues"
date: 2008-11-08
forum: General Help
---

### Post by Plasma_NZ on 2008-11-08
Ok heres the problem, grub was working fine...

Now its not... nothing has changed and no updates have been applied, and my keyboard works fine...

Here's the situation...

OK, when the pc boots, loads, grub comes up with my selection of what to boot...

Now i can press E or C etc or press enter, and those functions work fine, but as soon as i press a arrow-key to select a diff os to boot, grub freeze's, so currently the only way for me to boot into windows is to edit /boot/grub/menu.lst and put windows @ the top...

Again, my keyboard works perfectly fine, nothing has changed or been installed, no updates have been applied...

real hassle to oot between the 2 os's now as i have to use the LIVE-CD to mount /boot/grub and edit menu.lst manually again..

HELP!!

---

### Post by anystupidname on 2008-11-08
If your BIOS has the ability to force a hard drive (re)detection that could help. Try updating your BIOS (if an update is available) and try re-installing grub. As far as I know there isn't an easy way to debug at that point in the boot.

---

### Post by Plasma_NZ on 2008-11-16
ok the problem has nothing to do with my bios...

Secondly i have re-installed grub, problem is still there..

The problem also arises when booting with recovery CD, when i get to the selection screen, i cant use the arrow-keys otherwise it freeze's.. it is not a hardware issue and the keyboard works fine in linux and windows..


any idea's?

---

