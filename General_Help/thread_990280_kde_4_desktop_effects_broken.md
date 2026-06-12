---
title: "kde 4 desktop effects broken"
date: 2008-11-22
forum: General Help
---

### Post by camrant on 2008-11-22
I just enabled desktop effects and now my screen is completely black with some outlines of windows that are open.  I am looking for a configuration file or terminal commands that I can edit that will disable these effects or revert back to default settings.  Anyone know where to go from here?

---

### Post by kdfox on 2008-11-22
I ran into the problem and found the answer in another thread, which I cannot now find, so I will post the answer but without attribution:

1. At the black screen press ctrl-alt-F1
2. Login
3. Type:
```
nano ~/.kde/share/config/kwinrc
```
4.Scroll down to the [Compositing] section and eit the line that says:
```
Enabled=true
```
so that it says:
```
Enabled=false
```
5. Press ctrl-O and then enter to save.
6. Exit by pressing ctrl-X
7. Go back to the black screen by pressing ctrl-F7
8.  Restart your window manager by pressing ctrl-alt-backspace.

---

### Post by maestrobwh1 on 2008-11-22
Hmmm, I wonder if this is relating to a similar issue I had.  I upgraded to the latest kde 4 using the PPA repo... and I had the same issue.  I had to change OpenGL to Xrender to get the effects to work... and they had worked with OpenGL previously.  The Intel video is capable of supporting it.  I switched to Xrender... then OpenGL and it worked.

Which is "faster"  I assume OpenGL.

I do like the Xrender option.  It lets me use the effects on my laptop which has a crappy SIS card.

---

### Post by kdfox on 2008-11-23
I'd like to try Xrender, can you post a little how-to for going from one to the other?

---

### Post by maestrobwh1 on 2008-11-23
I just posted this to Kubuntu Forums as per your suggestion:-)

There seems to be little about it so I just did my best.  I tend to be verbose.  Teachers, we can never go for the short explanation!

[http://kubuntuforums.net/forums/index.php?topic=3099721.0](http://kubuntuforums.net/forums/index.php?topic=3099721.0)

---

