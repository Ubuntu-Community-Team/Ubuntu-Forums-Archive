---
title: "Broken Firefox!"
date: 2008-08-27
forum: General Help
---

### Post by mysterio2004173 on 2008-08-27
The back and forward buttons are grayed out. Also, the bookmark toolbar is no longer works... This has happened to me before on windows, I think it is some kind of bug in Firefox 3. Please help!

EDIT: Also, I need help clearing some HD space... Idk how it filled up so quickly... I think it was when I tried QEmu. Is there a way to completely remove QEmu?

---

### Post by mocoloco on 2008-08-27
Never seen that issue, but you can try starting Firefox in "safe mode". Before you do that you can backup your current Firefox settings (which would include bookmarks, add ons, etc) with this.
 Open a terminal and type
```
cp -r ~/.mozilla/firefox ~/.mozilla/firefox-backup
```
Then run safe mode with this
```
firefox -safe-mode
```
Try the option to reset toolbars and controls.

For your space issue, it could be all kinds of things, so maybe first see where you space is being used: Applications -> Accessories -> Disk Usage Analyzer
You can scan your home folder or the entire filesystem and find out where you space is going.

---

### Post by Crafty Kisses on 2008-08-27
Try running Firefox in the Terminal, see if you get any errors.

---

### Post by danny_galaga on 2008-08-28
this just happened to me too. at the same time my bookmarks stopped working. also, openoffice didnt want to save anything. that provided the clue- it said something along the lines of not being able to backup because there was no disk space on such and such a folder. id quote the whole thing but ive fixed the problem now! i now have bookmarks, forward/back AND i can use openoffice.

i deleted my mame roms folder to create some space. i dont know why i dont have enough space though. ill pose that in a new thread. anyway, see if you can get rid of some unwanted files before fiddling with settings. if that works, find out how to increase the space of your home folder (",)

---

### Post by mocoloco on 2008-08-28
Interesting, so maybe it is a disk space issue.  If so, [clear out unnecessary stuff]("http://ubuntuforums.org/showthread.php?t=140920").

I also found a good [brainstrom idea]("http://brainstorm.ubuntu.com/idea/57/") on this subject.

---

