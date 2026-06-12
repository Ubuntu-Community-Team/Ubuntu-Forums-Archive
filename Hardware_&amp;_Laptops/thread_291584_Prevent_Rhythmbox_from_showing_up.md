---
title: "Prevent Rhythmbox from showing up?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by juraj on 2006-11-02
I googled and searched for this but haven't found a clue. I'm using my ipod shuffle primarily as a storage device and it, uh, irritates me when rhythmbox shows up whenever I plug in my ipod.

Can I somehow disable that?

Thanks in advance, :)

---

### Post by billputer on 2006-11-02
This is a pretty easy solution.   Type "gconf-editor" into either terminal or the run command (Alt-F2).  Then expand "desktop" then "gnome", and finally, click on "volume_manager".  On the right it will say "autoipod" with a checkbox on it.  Uncheck the box, and you're good to go.

---

### Post by juraj on 2006-11-03
Thank you on your answer! I think a bug should be filed to get this into GUI.

---

