---
title: "Can't switch user."
date: 2008-09-05
forum: General Help
---

### Post by Windows_Apple_Linux on 2008-09-05
hey folks,
well I created a account for my mom and every time I want to switch user I just get a black screen (and which I have to press the reset bottom on the computer case because it doesn't allow me to do anything) any ideas?

---

### Post by Theberge43 on 2008-09-06
I have the same exact problem ... really annoying.

---

### Post by mnavasuk on 2008-11-19
I'm been having the same problem. Using hardy, ATI built in graphics, with proprietary drivers. I have 1 sudoer and two non sudoers users. If the sudoer user logs in (user A), then using the Fast user Swith applet, switch to the non sudoer (user B), so far so good. Then when user B logs off, the machine goes to a blank screen, only reboot button will restore to a working state.
I've tried using Ctrl+Alt+F1, F2, etc, or F7. Still, only reboot will cure.
Any suggestions?

---

### Post by mnavasuk on 2008-11-19
Some of my current settings:
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 1.4 (2.1.7412 Release)

~$ glxinfo |grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

and attaching Xorg latest log

---

