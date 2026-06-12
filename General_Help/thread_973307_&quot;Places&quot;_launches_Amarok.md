---
title: "&quot;Places&quot; launches Amarok"
date: 2008-11-06
forum: General Help
---

### Post by faintscrawl on 2008-11-06
I've got a weird problem. If I click on anything in the PLACES menu on the top bar, Amarok launches, AND I am unable to browse my files, like 'Home', etc.

---

### Post by faintscrawl on 2008-11-06
I uninstalled Amarok. Now when I go to PLACES-->HOME I get an error. Please see my screen shot.

---

### Post by faintscrawl on 2008-11-07
If anyone can help me out with this, I'd really appreciate it. 

THanks.

---

### Post by mc4man on 2008-11-07
This was a bug that was fixed but in some cases the you still need to manually address.
Find yourself a folder and right click -> properties -> open with. Choose 'open folder' and you should be ok. (make sure your updated)
You can re install amarok and there should be no further issues if you r. click on a folder of tunes -> open with amarok

If you don't have a folder available create one on your desktop and use  that

---

### Post by rbc on 2008-11-07
In terminal, type: nautilus

When the window opens, click on the up arrow. There should be a listing of your user directory. Right click on it, and go to properties. Then go to the Open With tab, and make sure "Open Folder" is there and the button is clicked. If it isn't there, click on Add (at the bottom of the tab). Search for Open Folder, and add it, then click that button

---

### Post by mc4man on 2008-11-07
If you have any problems after adding additional apps to the r.click -> open with menu the run and post this (you shouldn't

```
cat ~/.local/share/applications/mimeapps.list
```

the line in question is inode/directory=

---

