---
title: "Desktop rotation problem"
date: 2008-08-16
forum: Hardware
---

### Post by Radonballoon on 2008-08-16
I have a Lenovo X61 Tablet and so far I've gotten the laptop to recognize and rotate the screen whenever I rotate the laptop, but when it's rotated there are two problems:

1) The screen width and height are the same so half of the screen is cut off and the bottom half is completely black.
2) I can't click anything (mouse still works, stylus still works), nothing responds.

Any ideas?

---

### Post by racvets1 on 2008-08-18
Hello.  I actually had a similiar problem I had today.  I tried rotating my desktop using System>Preferences>Screen Resolution.  I had the same nothing responds like you did.  What I did to fix it:

1. Hit Ctrl+Alt+F2, and login.
2. cd ~/.gnome2/
3. mv monitors.xml monitors.xml.bak
4. Reboot ("sudo reboot now")

This makes a backup copy of your monitors.xml, and removes the original version.  It got me back to the normal window manager.  Hope it helps a little!

---

### Post by Radonballoon on 2008-08-18
Thanks for the reply. Unfortunately I couldn't apply your fix. In my gnome2 directory I don't have a monitors.xml file, only a backgrounds.xml file. I tried moving that one instead but it didn't do anything. Any more suggestions?

---

### Post by chayzer on 2008-08-28
Do you have compiz running? If so, disable it.

System -> Preferences -> Appearance -> Effects -> None.

---

### Post by Radonballoon on 2008-08-28
Yeah I finally figured that out, and I found a patch to allow compiz + rotation. Here's the link for anyone that may have this issue:[https://bugs.launchpad.net/mesa/+bug/132065]("https://bugs.launchpad.net/mesa/+bug/132065")
Just scroll down for the patches depending on your version of compiz

---

