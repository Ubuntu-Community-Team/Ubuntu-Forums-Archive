---
title: "can't install tint"
date: 2008-10-11
forum: General Help
---

### Post by Frozzare on 2008-10-11
hello, i can't install tint when i try to install it. i get an error.

mkdir -p /usr/bin
mkdir -p /etc/xdg/tint
install tint /usr/bin
install: cannot stat `tint': No such file or directory
make: *** [install] Error 1

what to do?

---

### Post by Frozzare on 2008-10-13
any who can help?

---

### Post by ChimpofDOOM on 2008-10-13
Well as much that I've never heard of the game or tried to install it, but i'll start with the usual routine of...

are you installing while in sudo mode?

---

### Post by Frozzare on 2008-10-13
no, not the tint tetris game
this, the panel
[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)

---

### Post by ChimpofDOOM on 2008-10-14
> **Frozzare said:**
> hello, i can't install tint when i try to install it. i get an error.

mkdir -p /usr/bin
mkdir -p /etc/xdg/tint
install tint /usr/bin
install: cannot stat `tint': No such file or directory
make: *** [install] Error 1

what to do?

Hehe my mistake, right.. looking at the documentation

Do you have all the requirements, cairo, pango, glib, imlib2 and xinerama?

As for what you have above, the documentation says to cd to src, type make and as root (sudo) make install.

I can't try this just now, until I get onto my Ubuntu machine thats 1. got a net connection and 2. up to date (yay for moving)

---

### Post by kowic on 2008-11-25
I had exactly same problem. any suggestions ? :(


EDIT: I fixed and installed succsessfully. There were still some missing libs :).
thanks to this thread: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=901930](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=901930)

---

