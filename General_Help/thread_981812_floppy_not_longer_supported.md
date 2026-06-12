---
title: "floppy not longer supported?"
date: 2008-11-14
forum: General Help
---

### Post by AGSzabo on 2008-11-14
hi,

i encountered a problem when inserting a floppy disk. it does not appear on the desktop. whats wrong?

greetings
AGSzabo

---

### Post by plucky on 2008-11-14
> **AGSzabo said:**
> hi,

i encountered a problem when inserting a floppy disk. it does not appear on the desktop. whats wrong?

greetings
AGSzabo

They forgot to load the drivers.

Try this ```
sudo modprobe floppy
``` and see if the floppy is then available.

To make sure it loads after a reboot ```
gksudo gedit /etc/modules
``` and add the word **floppy** on a new line.


Good Luck

---

