---
title: "[SOLVED] Alt Key Problems"
date: 2008-10-22
forum: General Help
---

### Post by anachronon on 2008-10-22
I am using an older version of Photoshop on Ubuntu 8.04.  My problem is that I can't use **[COLOR="Blue"]ALT[/COLOR]** as a hotkey.  Quite a few functions depend on the use of ALT.

Has anyone else had this problem with either Photoshop or other software?  Is there a setting that I need to change?  If so, which one, how do I find it, etc?

---

### Post by anotherdisciple on 2008-10-22
This is probably not helpful, but don't you have to run Photoshop in Wine? That could be the Alt problem...

... and is there something that keeps you from using GIMP instead?

---

### Post by anachronon on 2008-10-22
> **anotherdisciple said:**
> This is probably not helpful, but don't you have to run Photoshop in Wine? That could be the Alt problem...

... and is there something that keeps you from using GIMP instead?
Is there a problem with the ALT key in Wine?

---

### Post by anotherdisciple on 2008-10-23
Yeah... Wine does some weird stuff. Google "Wine Alt Key" and you'll find a lot of various problems. Sadly, I don't know a fix, but I bet Wine is the issue.

---

### Post by anachronon on 2008-10-23
> **anotherdisciple said:**
> Yeah... Wine does some weird stuff. Google "Wine Alt Key" and you'll find a lot of various problems. Sadly, I don't know a fix, but I bet Wine is the issue.
Thanks.  After doing a search, I found that all I needed to do was change a simple setting.  So, for anyone else reading this, here is the solution:

Linux , by default, uses the ALT key, in conjunction with the right mouse button, to move the position of a window.  Go to [COLOR="Blue"]System>Preferences>Windows[/COLOR].  At the bottom of that dialog box is the section, "Movement Key", with 3 radio buttons, "Control", "Alt", and "Super".  Change the selection to "Super" (which is the Windows logo key).  This frees-up the Alt key, without losing any Linux functionality.  Appropriately, the "Windows" key can now be used to move windows.

---

