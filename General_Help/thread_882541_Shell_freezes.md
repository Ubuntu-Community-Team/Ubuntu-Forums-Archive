---
title: "Shell freezes"
date: 2008-08-07
forum: General Help
---

### Post by Keith12125 on 2008-08-07
When I start gnome-terminal the window opens but it freezes before it's finished starting. After it locks up the only way to close it is to force quit. I doubt this is a problem with gnome-terminal because gedit (with the bottom pane terminal) does the same thing. Other apps that seem to be dependent on the terminal act in the same way.

When I boot the computer I don't have any problems until I open firefox (v2.0.0.16). After that theres nothing I can do to fix it other than restart.

I was wondering if anyone could point me towards a bug report and/or a solution if this is a common problem.

PS: I'm running Hardy Heron (v8.04)

Thanks, Keith

---

### Post by Crafty Kisses on 2008-08-07
Post the following output:
```
top
```
You might want to give system specs as well.

---

### Post by Keith12125 on 2008-08-08
Intel P4 3.00 Ghz w/ HT
ATI radeon x1950 512 MB
1.5 GB ram

---

### Post by Crafty Kisses on 2008-08-08
Have you tried Opera?

---

### Post by Keith12125 on 2008-08-28
I seem to have fixed my problem. The bottom pane shell plugin for gedit will cause this issue any time it encounters an infinite loop. I've heard of other shell plugins but I've just been using gnome-terminal; I havn't had this issue since I switched.

---

