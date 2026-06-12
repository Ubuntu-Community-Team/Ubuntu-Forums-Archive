---
title: "how to program hotkeys?"
date: 2012-09-11
forum: Hardware
---

### Post by N00b-un-2 on 2012-09-11
I can not find any information regarding this, just the file that needs to be edited.
i have a laptop which has some hot keys for launching a web browser, mail client, reloading a web page, etc.  what I would like to be able to do is to identify their keycodes and then program them manually.  For LIRC, you can use 'irw' to get terminal feedback from buttons to identify them and create a keymap.  I'd like to be able to do the same using my hotkeys some how.  Obviously this poses a problem because all the normal keys report to the terminal on their own, but pressing any of those buttons in a terminal window does nothing.

EDIT

Found the first part of what I'm looking for.  The application is 'xev'.  unfortunately it spits out mass amounts of information and it will take me a while to sift through it to produce something useful.  It would seem that 6 out of seven hotkeys on my computer are recognized, so that is a start.

EDIT 2

sudo showkey also reveals some useful info.  now to figure out how to map functions like opening "Kontact" with the mail button or a browser with the planet button.

---

### Post by N00b-un-2 on 2012-09-12
using xev to identify the keys I was able to map their keycodes to an ascii character with xmodmap.  Then from there I mapped the hotkeys to functions in KDE.  I'm sure there is a similar function in GNOME but since I jumped ship when the Unity/Shell bomb was dropped on GNOME, I don't know or care.  I'd like to find a way to make an xmodmap like change system wide, but since I'm the only one who uses this computer, it's not a big deal.

---

