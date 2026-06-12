---
title: "[SOLVED] default at boot"
date: 2008-11-18
forum: General Help
---

### Post by Bigneil on 2008-11-18
Dual boot, Xp then Hardy heron, how do i ask Grub to make xp default((wife)), and to extent the time to choose ubuntu.

---

### Post by Bigneil on 2008-11-18
sorry, i meant, extend the time before xp auto starts

---

### Post by sisco311 on 2008-11-18
If you want a GUI app to configure the settings, then install startupmanager.

Or you can edit the menu.lst file manually:
```
gksu gedit /boot/grub/menu.lst
```

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default         0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout         3**
...


---

### Post by Marius Derekus on 2008-11-18
> **Bigneil said:**
> Dual boot, Xp then Hardy heron, how do i ask Grub to make xp default((wife)), and to extent the time to choose ubuntu.

Ha ha ha ha! I pitty you. :lolflag:

---

### Post by Bigneil on 2008-11-18
Cheers buddy  :popcorn:

---

### Post by Bigneil on 2008-11-18
> **Marius Derekus said:**
> Ha ha ha ha! I pitty you. :lolflag:
  wife or xp?????

---

### Post by Bigneil on 2008-11-18
> **sisco311 said:**
> If you want a GUI app to configure the settings, then install startupmanager.

Or you can edit the menu.lst file manually:
```
gksu gedit /boot/grub/menu.lst
```

for manual......do i type this into the terminal or do i do it in start up??

---

### Post by maybeway36 on 2008-11-18
You type it into the terminal once you are in GNOME.

---

### Post by Marius Derekus on 2008-11-18
Xp and wife (only in the fact that she's dooming you with xp)

---

### Post by sisco311 on 2008-11-18
> **Bigneil said:**
> for manual......do i type this into the terminal or do i do it in start up??

Type it in a terminal.

The command will open the file(as root) in the text editor.

Edit the **bold** lines to fit your needs.

*default 0* means to boot the first grub menu entry
*default 1* means to boot the second ...

---

### Post by Bigneil on 2008-11-18
Thaks you guys.  i now have Ubuntu and windows set up just right  :cool::cool:

i will leave thanks in the proper place :wink::wink:

---

### Post by Bigneil on 2008-11-18
> **Marius Derekus said:**
> Ha ha ha ha! I pitty you. :lolflag:


LOL LOL CLUNK!! the penny drops. i wouldn't want xp as my default wife either LOL

---

### Post by Marius Derekus on 2008-11-18
> **Bigneil said:**
> LOL LOL CLUNK!! the penny drops. i wouldn't want xp as my default wife either LOL

:lolflag: again.  Glad to hear that your issue's been solved. (In the fact that you got the booting problem fixed.)

---

