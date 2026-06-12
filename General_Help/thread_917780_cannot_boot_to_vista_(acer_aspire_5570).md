---
title: "cannot boot to vista (acer aspire 5570)"
date: 2008-09-12
forum: General Help
---

### Post by alwhit on 2008-09-12
I installed Ubuntu on a separate partition
to have both vista and the Linux operating system.
When I boot the computer
the dual boot comes up 
and I select windows.
Instead of loading vista
it goes the Acer eRecovery Manager.
I reinstalled(?)vista using acer recover 
disks but it still loads Acer Recovery Manager
and not vista
How do I get it to load vista.
Or how can I reformat so that 
Ubuntu is deleted and 
Vista is not deleted.

---

### Post by tekky on 2008-09-12
Usually this doesn't mean you have to reformat 100 times or do anything different.  It means the grub isn't setup correctly.  A lot of the new computers have a hidden partition that is used for resetting the computer back to factory settings since people keep losing disks and such.  So, my best educated guess would be that in your grub instead of 'windows' pointing to the windows partition it's pointing to that recovery partition.

Check your Menu.lst and make sure that 'windows' points to the correct device.

---

### Post by alwhit on 2008-09-12
Thank you Tekky
I don't know how to find 
Menu.lst.
Please tell me how to do that.

---

### Post by alwhit on 2008-09-12
I did the following:
clicked on pqservice,
clicked on autorum
boot, grub then
menue.1st
menue.1st seems to be instructions that I don't understand.

---

### Post by alwhit on 2008-09-12
I now have file: /boot/grub/menu.1st
and a blinking square underneath.
What do I do now?

---

