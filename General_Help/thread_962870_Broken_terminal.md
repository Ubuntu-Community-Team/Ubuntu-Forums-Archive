---
title: "Broken terminal"
date: 2008-10-29
forum: General Help
---

### Post by alankennedy100 on 2008-10-29
Hi all

I am using Ubuntu 8.04.

My terminal has suddenly stopped working, it opens the window but the prompt never becomes useful. And if I leave the window open for to long the whole system freezes.

The last updates of the system where apt, from today, so maybe that broke the terminal... I tried loading the virtual consoles with alt + Fx but the same happens, the prompt never becomes useful!

Does anyone know how can I get a clue of what has caused this, or how I can fix the system??

Thanks in advance!!

---

### Post by geirha on 2008-10-29
If you create a new user and log in with that. Does the terminal work for that user?

Sounds like there could be some bad code in ~/.bashrc, ~/.bash_profile or /etc/bash.bashrc ... assuming you are using bash as your default shell.

---

### Post by alankennedy100 on 2008-10-30
Hi Geirha

I tried the terminal for another user, and it was the same problem.

Any other suggestions? I really need my terminal back!

---

### Post by geirha on 2008-10-30
Hm, does hitting Ctrl+C do anything (when the shell is hanging)?

---

### Post by alankennedy100 on 2008-10-30
That did have an effect, I got my prompt, but is not totally functional.

For example using git just hangs there, until I do a Control C. I tried opening gedit and it did open, but it froze the system quickly and I had to hard reboot.

One good news is that vim worked. Any more ideas??

Thanks for help!

---

