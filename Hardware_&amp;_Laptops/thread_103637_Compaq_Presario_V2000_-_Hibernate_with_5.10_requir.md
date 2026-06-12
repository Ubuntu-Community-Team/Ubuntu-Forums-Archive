---
title: "Compaq Presario V2000 - Hibernate with 5.10 requires no &quot;splash&quot; kernel arg"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by peterw on 2005-12-14
It took a good bit of searching these forums and other sites before I figure out how to make Hibernate work with Breezy Badger 5.10

After my initial install, Hibernate was offered as an option in the Log out menu. It seemed to hibernate, but resuming did not work. I saw a message about needing a resume= kernel option, so I added that. Resume from Hibernate still froze after reading pages from disk and announcing a need top copy pages.

The solution seemed to be simply removing the "splash" kernel boot argument in menu.lst. With no "splash" option, I have a basic text mode boot sequence instead of the more attractive graphical Ubuntu boot sequence, but Hibernate works.

I have this and more documented at [http://www.tux.org/~peterw/v2000/](http://www.tux.org/~peterw/v2000/)

---

### Post by wwbdd on 2005-12-14
I just purchashed a new v2000 as well but mine has the turion instead of the intel chip.  When I tried the live cd to see what would be recognized the x server failed.  Any words of advice?  Should the install process take care of that even though the live cd doesn't?

Now that i look back at your link you have a different graphics card so you may not have had this problem.  I have the ati radeon 200 xpress.

---

