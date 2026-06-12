---
title: "Xmodmap In full screen Terminal"
date: 2008-11-16
forum: General Help
---

### Post by transmition on 2008-11-16
I run Ubuntu 8.10 on my macbook, and have an Xmodmap file that switches my command and control keys. When I log into the gnome desktop, this works fine, but when I enter the full screen terminal, this does not carry over. How can I load the Xmodmap file while in the shell?

On a related note, what is the proper name for the full screen terminal?

---

### Post by transmition on 2009-01-31
Additional information / Rephrase:

Is it possible to load an Xmodmap without GDM/X?

---

### Post by Dr Small on 2009-01-31
For screen terminal as in Virtual Terminal (CTRL + ALT + F1) ?

---

### Post by transmition on 2009-01-31
I am referring to the environment you are in when you do not have gdm or X running.

So, not a virtual terminal.

Sorry for any confusion.

---

### Post by Dr Small on 2009-01-31
Well, if X or GDM is not running, the only thing left *is* a virtual terminal. But you can not use xmodmap in the command line, since xmodmap requires Xorg to be running.

---

