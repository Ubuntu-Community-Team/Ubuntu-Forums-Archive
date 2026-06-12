---
title: "GRUB menu question"
date: 2008-10-29
forum: General Help
---

### Post by rmcellig on 2008-10-29
When I set the timeout to let's say 20 seconds in the Startup manager, upon startup A notice appears to press the ESC key to get to the boot loader menu. Is there anyway when I startup that I don't have to press the ESC key and just go the the bootloader menu with the 20 second countdown showing?

---

### Post by rmcellig on 2008-10-29
I solved my problem. Thanks anyway.

---

### Post by bryonak on 2008-10-29
Just for the record, you might want to include the solution, so other users who search for the subject will see it too...

You can do this by pressing alt+f2 and entering 'gksudo gedit', in order to open GEdit as root (system administrator).
Then hit ctrl+o and open File System -> boot -> grub -> menu.lst
There are a lot of options, among them 'hiddenmenu', which you can turn off by prepending a # (comment delimiter) in front of it. Now save and the GRUB menu won't require pressing esc.

A slightly faster way is via terminal: sudo nano /boot/grub/menu.lst

---

### Post by rmcellig on 2008-10-29
Actually it was an option in the menu,  System/Administration/Startup-Manager. Under Misc. Make sure that Show bootloader menu is selected.

---

### Post by bryonak on 2008-10-29
Right, that's a good alternative too, if one prefers a GUI (as most users do nowadays).

But you have to install the Startup Manager first, since it isn't included in Ubuntu's default setup (Hardy that is)... either via Synaptic or in a terminal: sudo aptitude install startupmanager

---

### Post by nazrysamaratin on 2008-11-08
> **bryonak said:**
> Just for the record, you might want to include the solution, so other users who search for the subject will see it too...

You can do this by pressing alt+f2 and entering 'gksudo gedit', in order to open GEdit as root (system administrator).
Then hit ctrl+o and open File System -> boot -> grub -> menu.lst
**There are a lot of options, among them 'hiddenmenu', which you can turn off by prepending a # (comment delimiter) in front of it. Now save and the GRUB menu won't require pressing esc.**

A slightly faster way is via terminal: sudo nano /boot/grub/menu.lst

how can i turn off 'hiddenmenu' in my GRUB 
newbie here

---

### Post by nazrysamaratin on 2008-11-08
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

