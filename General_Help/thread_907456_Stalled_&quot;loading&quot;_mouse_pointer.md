---
title: "Stalled &quot;loading&quot; mouse pointer?"
date: 2008-09-01
forum: General Help
---

### Post by iaggrey on 2008-09-01
If you click on a program, you see the mouse pointer turn into the loading dial, right?

My problem is that the loading dial doesn't turn back into the regular mouse pointer when I'm on the desktop (even after restart/shutdown). It's just perpetually in its loading form on the desktop, but the pointer is fine when in other programs as far as I can tell.

I've looked through my terminal history and I can't see anything that would have caused the problem (since I installed and then uninstalled the same program before the issue started as far as I know). It doesn't seem to be making my computer run slower, but it's kind of annoying...and I prefer to leave a fresh install as the very last option.

Anyway, I know this question is kind of vague, but does anyone know how to solve this issue? 


(Running 64-bit edition of Ubuntu 8.04 on an HP Pavillion dv5t-1000 laptop.)

P.S. I'm new to Linux so if you have a very technical solution, then please go through each step.

Thanks in advance!

---

### Post by conorsulli on 2010-12-22
bump I have this problem and would rather not make a duplicate If it can be solved here :-(


**edit**

Oddest possible fix: (note that not even reboots helped) I am going to show what I did exactly as I cant re-produce the problem again:

Quit pidgin and awn ... it still ran
run command: xkill click the desktop (kills nautilus) 
run command: **xkill **click the top **gnome panel** repeat for the bottom if you have one.. it reloads and the loader went away then even after reboots :-/

I would imagine it was when I did the **xkill on gnome-panel so you may want to try that first**.

I know its an odd fix but if it helps and fixes somebody elses mouse then all the better as it was very annoying!

---

