---
title: "Synaptic doesn't run through gksudo? (Solved)"
date: 2005-11-19
forum: General Help
---

### Post by spirilis on 2005-11-19
For some reason when I select Synaptic through the menus it doesn't seem to run.  gksudo does ask me for my password, doesn't complain, but nothing happens and synaptic doesn't run.

Running gksudo synaptic from a terminal shell results in the command completing immediately.  The exit code is 0.

I can run synaptic if I su up to root and run it from there.
What gives?

---

### Post by spirilis on 2005-11-19
[QUOTE=spirilis]For some reason when I select Synaptic through the menus it doesn't seem to run.  gksudo does ask me for my password, doesn't complain, but nothing happens and synaptic doesn't run.

Running gksudo synaptic from a terminal shell results in the command completing immediately.  The exit code is 0.

I can run synaptic if I su up to root and run it from there.
What gives?[/QUOTE]
Nevermind, found it.  I didn't have /etc/sudoers set up--probably 'cause I set a root password during 'expert' install. ;)

---

