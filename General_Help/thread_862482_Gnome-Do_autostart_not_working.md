---
title: "Gnome-Do autostart not working"
date: 2008-07-17
forum: General Help
---

### Post by Jorhajnes on 2008-07-17
I'm having a bit of problem getting Gnome-Do to autostart. 
Each time I check the box "Start GNOME Do at login" it gets unchecked as soon as I close the window. 
Tried doing it by starting the program in a terminal with sudo, not working either but I got an error in the terminal:
"Failed to set autostart: Directory not found"

Anyone who might know which directory this might be and perhaps where to get it?
Tried making a fresh install to but that doesn't help...

Thanks.

---

### Post by joshsmith on 2008-07-18
hi
dont do it through gnome-do
use the centralised place for autostarting applications, namely:
system>preferences>sessions

then add a new program with the command
gnome-do --quiet
(use quiet so you dont see the window till you do the key combination)

---

### Post by Jorhajnes on 2008-07-20
Worked like a charm.

Thanks!

---

