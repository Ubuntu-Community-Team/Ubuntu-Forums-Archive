---
title: "Kubuntu"
date: 2005-11-19
forum: General Help
---

### Post by Drifter on 2005-11-19
I just got the Kubuntu live cd and I am using it right now.  I have ubuntu installed on one of my harddrives.  Question, can KDE desktop be installed when you have gnome with ubuntu.  Thanks

---

### Post by qalimas on 2005-11-19
sudo apt-get install kubuntu-desktop

---

### Post by Drifter on 2005-11-19
I like gnome but I also like kde and would like to try it.  Will this be reverseable if I do it.

---

### Post by aysiu on 2005-11-19
Reversible in what sense?
Even after you install kubuntu-desktop, you can still choose whether you want to log into Gnome or KDE. That's the beauty of it.
However, if you ```
sudo apt-get remove kubuntu-desktop
```, that'll essentially do nothing, as kubuntu-desktop is not a real package--it's a "meta-package" that really tells apt-get to install a bunch of other things.

---

### Post by Drifter on 2005-11-19
OK thanks, I will give it a try.  I like that u can log in for either one.

---

