---
title: "editing .profile won't let me log in"
date: 2008-11-10
forum: General Help
---

### Post by RedWagon on 2008-11-10
if I add anything to /home/verdow/.profile when I log on my computer freezes at a black screen with just the mouse and I have to Ctrl-Alt-Backspace out, log into Failsafe Terminal, fix .profile then log back in.  All I do to .profile is add
pidgin & 
and it doesn't work.  Compiz is kind of messed up on load (I've had it happen before) and usually adding 
compiz-switch &
or
compiz --replace & 
to fix it but those do the same thing.

---

### Post by taurus on 2008-11-10
Instead of adding programs to your ~/.profile (which is not a good idea), why not add them in System -> Preferences -> Sessions?

---

