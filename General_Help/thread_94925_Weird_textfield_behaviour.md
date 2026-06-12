---
title: "Weird textfield behaviour"
date: 2005-11-25
forum: General Help
---

### Post by mathijs on 2005-11-25
Ubuntu works fine for me, except that the text cursor (caret) is copying itself in firefox and openoffice. When I type something, and then start moving around with the arrow keys, the old text cursor doesn't get erased. 
I've noticed there are multiple threads about this issue(see below), but none mentions a solution.
I have a nvidia graphics card, and use the nv x.org driver. The strange thing is that it doesn't happen at all in terminals, kedit, gedit, or any other program I tried. Only in firefox and openoffice.

Other threads about the same thing (I think):
[http://www.ubuntuforums.org/showthread.php?t=91017](http://www.ubuntuforums.org/showthread.php?t=91017)
[http://www.ubuntuforums.org/showthread.php?t=84914](http://www.ubuntuforums.org/showthread.php?t=84914)

---

### Post by jaypeasy on 2005-11-25
I would recommend installing the proprietary binary drivers for your nvidia graphics card. It is in the ubuntu repositories, so installing is trivial. It should automatically modify your /etc/X11/xorg.conf to use the nvidia driver.

---

