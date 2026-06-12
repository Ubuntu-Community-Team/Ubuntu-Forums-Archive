---
title: "How do I salvage Sent Messages in Evolution"
date: 2008-08-07
forum: General Help
---

### Post by jsym on 2008-08-07
Apparently my "Sent" folder has gotten too big for Evolution to handle after many years of use (2+ GB).  I can no longer see it on the left-hand tree and every time I send a message I receive the following error message:
```
Failed to append to mbox:/home/USER/.evolution/mail/local#Sent:
Cannot get folder `Sent': Value too large for defined data type
Appending to local `Sent' folder instead.
```
I've looked around on bugzilla and [I am not the only one with this problem]("http://bugzilla.gnome.org/show_bug.cgi?id=540574"). Unfortunately no solutions have been offered.

**Is there a way for me to salvage recent things out of my sent mail folder while ditching the old stuff so that Evolution can handle it again?**

---

### Post by rbmorse on 2008-08-07
You can ditch old stuff from the "Sent" folder. It's a two step process. 

First select and delete unwanted messages from the "Sent" folder

Then, select the "Trash" folder, go to the menu bar at the top of the window, select "folder" and then click on "expunge."  For reasons known only to the Evilution devs when you delete something in Evolution, it doesn't get deleted until you go back and "expunge" the folder.  I'm sure they have their reasons.

---

### Post by jsym on 2008-08-11
Unfortunately the "Sent Mail" folder no longer exists in the left-hand tree so I can't go into as I normally would and delete messages directly.  I would LOVE to do this, but since I can't see the folder I don't know how.

:(

---

### Post by Fidelio on 2008-10-02
Does anyone have a solution for this? One of my saved email folders contains a lot of audio for a project I've been working on and now I can't access it at all! This is a really big problem for me.
How big does the folder have to be before it locks up? Is there any way I can access the folder and split it? Any answers?
Many thanks in advance,
Andy

---

