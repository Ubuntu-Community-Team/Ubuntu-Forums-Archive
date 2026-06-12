---
title: "Acer Aspire One Screen Rotation"
date: 2008-09-20
forum: Hardware
---

### Post by mikeRimex on 2008-09-20
I'm having trouble with screen rotation with my Acer Aspire One running Ubuntu. I want to be able to hold it like a book.

I use the /Preferences/Screen Resolution applet, to try and rotate the screen, it rotates but is a but screwed up. The mouse pointer responds, but no clicks or keystrokes seem to register.

any ideas?

---

### Post by filipecamargo on 2008-09-21
I have the same problem with my Acer Aspire 5570Z.
I used to use "Irotate" for windows for that but I still not found a solution for Ubuntu! I'm looking forward!
Let me know if you find one!
Thanks!

---

### Post by protozoo on 2008-09-22
Hi,

same here, running Ubuntu 8.04.01 in an Aspire One.
Is there a way to restore the default orientation? Right now, each time i log-in Ubuntu the screen gets rotated and i'm unable to use it.
Keyobard seems inactive, although i could jump to a console view (Ctrl+Alt+F1) and opened xorg.conf in VIM, but looks like there's nothing i can edit there about rotation.

Thanks!

---

### Post by protozoo on 2008-09-22
Hi again,

just managed to restore the orientation. On login screen, click Options and change session to GNOME safe mode, then log-in.
This opened the desktop rotated, but this time mouse and keyboard worked ok. This allowed me to get to Settings/Screen resolution dialog and restore the rotation mode to Normal.

Anyway, looking forward to being able to have the rotated view working properly.

Cheers.

---

### Post by protozoo on 2008-09-22
I tried again logging-in with GNOME failsafe mode, and yes, both mouse and keyboard works ok (aside synaptics pad doesn't rotate, making it difficult to operate).
So it seems something related to ther X script?

---

