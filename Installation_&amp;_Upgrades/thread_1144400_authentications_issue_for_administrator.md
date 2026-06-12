---
title: "authentications issue for administrator"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by bikeman1 on 2009-04-30
I just hopped to 9.04 from 7.04 and reinstalled from the ISO over the same partitions for root, home, and swap I had used before.  The install seemed to see a lot of my old destop and preserved it, though many of the links were obsolete.  However, the strangest thing is how it is treating me as the administrator.  First, when I set up the shell for administration, I used gksudo to load the shell, but it still seems to require sudo authentication throughout for each command.  For example, even a simple "fdisk -l" request is ignored until prefixed with a "sudo".  Second, I can't get users-admin to let me make changes to any users at all, including myself.  my username (call it mike) does have admin privileges and is able to do sudo tasks -- but no access to the users or groups.  I can change file permissions.

Does anyone know how I can regain or check my admin status?  Am I using the wrong terminal shell (gnome-terminal) or the wrong users program ??  This is weird.

Other than that 9.04 looks gorgeous....

---

