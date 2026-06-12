---
title: "[SOLVED] Open Office stopped using window manager/decorator"
date: 2008-10-15
forum: General Help
---

### Post by michaelkahl on 2008-10-15
The other night I was using open office to read a word document.  All of a sudden my windows manager/decorator was just gone from the window.  I've tried doing a purge of open office, then reinstall.  I've switched between emerald and gtk.  Still no luck, it just stopped using the manager/decorator. 
Any help is appreciated. 
Thanks

---

### Post by CJ56 on 2008-10-15
And you have made sure that Window Decoration in CompizConfig Settings Manager is still checked?

Sometimes it unchecks itself -

---

### Post by michaelkahl on 2008-10-15
Yes I have, and it is checked.
I'm using compiz as my manager and emerald as my decorator.
I've also tried metacity / gtk combo and that didn't work.
I even get the same problem in XFCE enviroment.

Also I've tried multiple themes, including human.

---

### Post by CJ56 on 2008-10-15
Erm...

Have you looked at this thread - 

[http://ph.ubuntuforums.com/showthread.php?t=920875]("http://ph.ubuntuforums.com/showthread.php?t=920875")

---

### Post by michaelkahl on 2008-10-15
Hadn't seen that thread, but I'm skeptical.  This is not my issue.  The issue only exist with openoffice.

Edit:  I checked and this line is added to my xorg.conf

---

### Post by CJ56 on 2008-10-15
Some people have tried unchecking 'Legacy fullscreen support' in the Workarounds section of CompizConfig Settings Manager... ?

---

### Post by michaelkahl on 2008-10-15
That did it, thank you so much for the help/support.
I really appreciate you taking the time today to help me out.

---

### Post by CJ56 on 2008-10-15
Glad it worked...!

---

