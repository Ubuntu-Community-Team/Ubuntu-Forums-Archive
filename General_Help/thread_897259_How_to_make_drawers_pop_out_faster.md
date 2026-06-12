---
title: "How to make drawers pop out faster"
date: 2008-08-22
forum: General Help
---

### Post by jmjohn on 2008-08-22
Hey all, I have what may be an easy question: is it possible to make drawers ( on the gnome panel) pop out faster than they do?  The speed is really just too slow for me.  

Thanks much!
glass.dimly

---

### Post by stinger30au on 2008-08-22
works fine on my pentium 4 3Ghz machine with 1.5 gig of ram.

having said that i bet there will be an option for it to make the drawers "snap" out rather then slide

---

### Post by stinger30au on 2008-08-22
i think i have found your answer, read this thread

[http://ubuntuforums.org/showthread.php?p=5641899#post5641899](http://ubuntuforums.org/showthread.php?p=5641899#post5641899)

---

### Post by jmjohn on 2008-09-08
Thanks for the response, but Ubuntu Tweaks contains no option for disabling the drawer slowness problem.  Even disabling panel animations didn't do the trick.

It's not life-shorteningly slow, but it's just too slow for me.

And I have a 2.3 Ghz Dual Core with 4 Gigs of RAM.

-glass.dimly

---

### Post by Gattsu on 2008-10-04
Create a file named .gtkrc-2.0 in your /home/user/ directory and type this line inside :

gtk-menu-popup-delay = 0

Save the file and restart your session.

This workaround also speeds up all Gnome menus by showing them with no delay. It's supposed to also affect drawers.

[_source_]("http://brainstorm.ubuntu.com/search?tags=drawers&ordering=mostvotes")

---

