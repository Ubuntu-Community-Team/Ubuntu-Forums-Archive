---
title: "weird colon-format version numbers?"
date: 2008-11-20
forum: General Help
---

### Post by teledyn on 2008-11-20
Why would a maintainer set the version number to a non-standard form like 1:1.6.1-1ubuntu1?  The 1: seems very non-standard -- I have been using Linux since 1994 and had never seen this convention before.

And this colon-format creates a versioning problem: the colon-char invalidates the natural sort order that would allow using the original project's 1.7.3 because aptitude will always consider "1:1*" to be newer than "1.7*".  Since the ubuntu package is pretty outdated, any serious use of this package (rosegarden) would want to upgrade to 1.7.x, but having done so, the new-updates notification icon (in gnome) becomes useless because it will *always* list 1:1.6.1 as the 'update' for 1.7.3.

I found an archive page package builder guide by Tamir that mentions the conventions for version numbers on debian and non-debian packages, but it makes no mention of this Ubuntu colon-version convention.  What is the meaning of the colon?  Is it used often in Ubuntu package versions? (I haven't noticed any others)  I contacted the package maintainer about this (logged a ticket) and my request was rejected; he is convinced the version number is valid and good.

Related to that, since I can't fix a distro package, I'm hoping to route around the problem, but I'm having trouble generating a package with a colon-version number; dpkg-builder sometimes takes it as a colon, sometimes escaped as a percent+hexcode and this conflicts with the dirnames.  How would I generate a package with this non-standard char in the version?  

Or perhaps more effective and less bother, is there some way to tell aptitude to *ignore* individual package updates so I can ban rosegarden-1:1.6.3-1ubuntu1 and handle my own updates on the 1.7.x version stream?

---

### Post by ajgreeny on 2008-11-20
Not sure about aptitude, but with synaptic you can use the **Package->Lock Version** in the menu and whatever you have will be locked, and no update notifications will appear.

---

### Post by teledyn on 2008-11-20
> **ajgreeny said:**
> ... with synaptic you can use the **Package->Lock Version** in the menu and whatever you have will be locked, and no update notifications will appear.

Excellent!  Thanks, this will do quite nicely!:)

---

