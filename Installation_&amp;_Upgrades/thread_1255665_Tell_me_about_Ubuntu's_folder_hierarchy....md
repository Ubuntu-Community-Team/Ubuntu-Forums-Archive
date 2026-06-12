---
title: "Tell me about Ubuntu's folder hierarchy..."
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by nbtrap on 2009-09-01
Where can I find information about Ubuntu's folder hierarchy? I'd like to know what kinds of files I should expect in what folders, where the various files of my packages are installed, where I should install various binaries, which folders are automatically linked to the GNome menu, how to associate certain icons with certain binaries etc. I know the very basic gist of what goes where, but I'd like to know more.

---

### Post by RedSingularity on 2009-09-01
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Thats a great site!

---

### Post by raymondh on 2009-09-01
> **Shadow121 said:**
> [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Thats a great site!

what a coincidence ...was just reading that site :)  +1

---

### Post by falconindy on 2009-09-01
+1! I was about to post the same link. Isn't Google grand?

When you're installing software, you're typically going to be doing it through a package manager or with `make install` after compiling from source. Both of these methods will take care of putting the binaries in the proper locations and possibly adding to the application menu.

---

### Post by nbtrap on 2009-09-01
Thanks for the site. I have a lot of reading to do. However, it doesn't say anything GNome or Ubuntu specific. For instance, I manually installed FileZilla the other day by dragging its bin ans share folder into /usr/local, where they merged with what was already there. What baffled me was that the program was automatically added to my menu, as well as to the list of programs in the "open with" menu. I don't understand how it knows what icons to link with what binaries, where to put the program in the menu etc.

---

