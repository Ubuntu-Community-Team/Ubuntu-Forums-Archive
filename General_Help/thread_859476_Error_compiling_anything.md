---
title: "Error compiling anything"
date: 2008-07-14
forum: General Help
---

### Post by Ataris on 2008-07-14
I don't have Internet access so I use a public computer and am forced to compile things.

When compiling anything, after I type in the configure line and then type in "make" i get something like ```
**** target not found
``` What is wrong?

---

### Post by mc4man on 2008-07-14
> What is wrong?  for starters you need a set of basic build packages installed on the machine. Then each app you try to build usually will require add. packages, sometimes dozens. Even if you could manage all that if you build off of a plain ./configure you may end up with build that won't install or run good on your machine.
Assuming you could add packages and repo's to the public machine then building off of the ubuntu repo source for your install would work if you used something like > dpkg-buildpackage -rfakeroot -uc -b or
> fakeroot debian/rules binary and make any configure changes in debian rules file instead of ./configure, make, sudo checkinstall --install=no or whatever you were planning.
Then you'd need to make sure you had the install deps satisfied on your machine
Seems like quite an impossible situation

---

