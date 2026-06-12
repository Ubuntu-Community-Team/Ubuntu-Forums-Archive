---
title: "How to start X Session without a manager?"
date: 2008-07-26
forum: General Help
---

### Post by uclalinux on 2008-07-26
How can I start a X session without having a window manger load?
I just want the bare minimum.

---

### Post by squaregoldfish on 2008-07-27
At the login screen, there should be an option to specify which type of session you want (gnome, kde etc.). One of those options will be failsafe, which does exactly what you're after.

Steve.

---

### Post by uclalinux on 2008-07-27
Thanks Steve, But that is not what I am looking for. If you install Gentoo, or a server edition with out an X on it, and added one later you will know what I mean. it is the default interface that comes with Xorg software. your mouse icon is an "x" marker and the window will usually have a white and black cross hatch or black.

---

### Post by Eck on 2008-07-27
Traditionally, that command would be:

startx

---

### Post by uclalinux on 2008-07-28
yes, but that will load gnome on ubuntu. I was hoping that there would be a command that would be able to load only a default X and nothing else.

---

