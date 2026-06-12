---
title: "man on amd64 9.04"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by dmallery on 2009-06-11
big:/home/dmallery>> man man
man: can't set the locale; make sure $LC_* and $LANG are correct
No manual entry for man
See 'man 7 undocumented' for help when manual pages are not available.

i can't read any man pages, with or without root.

this was an update-manager upgrade from the previous version in which man also did not work.

my searches on these forums turned up nothing.

any clue would be wonderful

thanks


dave

---

### Post by jimv on 2009-06-11
try this command:


sudo apt-get install --reinstall man-db

---

### Post by dmallery on 2009-06-11
tried it, but no cigar...

thanks


dave

---

### Post by dmallery on 2009-06-11
correction:  now it works with sudo, but not as non-root user!!

still needing suggestions..

thanks

dave

---

