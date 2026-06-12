---
title: "[SOLVED] Title Bar disappearing!"
date: 2008-11-20
forum: General Help
---

### Post by jbeaunaux on 2008-11-20
Recently I've been having an issue with Firefox and OpenOffice 3.0. When I launch either of these programs, the window they are opened in expands to the point where the title bar and the bar at the bottom of the screen disappear. I ran into this same problem with Firefox in Hardy, but after upgrading to Intrepid I hadn't had this happen until now. What can I do to fix this? Thanks!

---

### Post by kelean on 2008-11-20
Use the alt+mouse click to move the window to get to the maximise button on the title bar of the window.  That should do it.  I have had that problem before myself.  I hope that helps.

Kelean.

---

### Post by jbeaunaux on 2008-11-20
I tried that, but it didn't seem to work. When I pressed Alt 'File' would be highlighted on the tool bar and nothing else would happen when I tried to drag the window with the mouse. Maybe it's user error, seeing as I'm really new to Ubuntu... ;)

---

### Post by kelean on 2008-11-21
Try to right click on the tab for firefox on the bottom bar.  It should bring up a menu that has maximise on it. 
Kelean.

---

### Post by lifestream on 2008-11-21
Try hitting Windows key + F
Or F11 by itself
And/or both.

I've had this prob before as i upgraded to intrepid, it was really annoying. found out the fix by accident.

forgive my typos and grammar, im about to go to bed

---

### Post by jbeaunaux on 2008-11-21
Thanks to both of you for the pointers! It looks like hitting F11 does the trick for Firefox, but it doesn't work for OpenOffice. Any ideas on that one?

---

### Post by lifestream on 2008-11-21
Found this little gem of information:

On your file browser, make sure *View->Show Hidden Files* is enabled.

Go to your home directory (the one with your name).
Look for the folder *.openoffice.org2* and delete it, or rename it to something like .*openoffice.org2.backup*

I'm not sure if the folder still has the number 2 on it, since you're using version 3. I had this problem with version 3, but now I use v2.
But you'll know which folder it is.


**[COLOR="Red"]OR[/COLOR]**
Detele this file,** if it exists**:
>  ~/.openoffice.org2/user/registry/data/org/openoffice/Setup.xcu

The problem with that file is that it sets "window size" to your entire screen :P There's the culprit!

Credit goes to: [https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/32469](https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/32469)

---

### Post by jbeaunaux on 2008-11-22
I gave tried doing that and, well, it's still doing it. Maybe I need to completely reinstall ubuntu to get things to reset? Or is that too extreme?

---

### Post by jbeaunaux on 2008-11-24
Well, I seem to have found a fix - I installed Xubuntu, removed the Ubuntu desktop, and then reinstalled it. I've now removed Xubuntu and everything seems to be working fine. Thanks to everyone for their help!:)

---

