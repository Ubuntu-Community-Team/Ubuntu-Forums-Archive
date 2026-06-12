---
title: "[SOLVED] So what does the ubuntu-desktop package actually do?"
date: 2008-10-11
forum: General Help
---

### Post by Theo148 on 2008-10-11
I know that the 'ubuntu-desktop' package depends on all the other packages needed for Ubuntu's desktop environment, but it seems that it has a function other than being a metapackage. The package description says:

"It is also used to help ensure proper upgrades, so it is recommended that it not be removed."

Does anybody know what exactly this refers to?

---

### Post by aysiu on 2008-10-11
If the default packages change from one release to another, having the *ubuntu-desktop* package installed will make sure you get the new packages and have removed the obsolete ones. For example, Intrepid Ibex (8.10) now has this thing called "last working boot," and there's a package that handles that and adds it to the Grub boot menu. If you have *ubuntu-desktop* installed when you upgrade, you will get that package. If you don't have it installed, you'll just get newer versions of the packages you already have installed.

---

### Post by Theo148 on 2008-10-12
Thanks for the info! :) I guess I'll have to make sure I have that package before upgrading to 8.10.

---

