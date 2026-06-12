---
title: "[SOLVED] Set default Xterm size"
date: 2008-08-09
forum: General Help
---

### Post by jalirious on 2008-08-09
Hi, this has been marked as 'Solved' in a few posts, but .Xdefaults, etc, never worked for me.

Anyway, on Hardy..

1) Right-click on the terminal icon (on your toolbar/wherever)

2) Left-click on 'Properties'

3) Replace gnome-terminal with gnome-terminal --geometry 72x30

[72x30 is just height x width, vary to taste]

4) Click close.

Done.

---

### Post by pauper on 2008-08-10
xterm != gnome-terminal

As far as I know, ~/.Xdefaults is a custom resource file for X11 apps, which are
otherwise defined in /etc/X11/app-defaults files.

gnome-terminal custom settings are in ~/.gconf/apps/gnome-terminal and
~/.gconf/desktop/gnome/applications/terminal directories.

---

