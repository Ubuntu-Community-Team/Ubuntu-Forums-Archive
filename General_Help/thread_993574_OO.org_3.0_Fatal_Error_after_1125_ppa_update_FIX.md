---
title: "OO.org 3.0 Fatal Error after 11/25 ppa update FIX"
date: 2008-11-25
forum: General Help
---

### Post by anim on 2008-11-25
After the recent ppa update for OO.org 3.0, a fatal error occurs on Open Office program launch. 

to fix, remove the openoffice.org-gnome package
```
sudo apt-get remove openoffice.org-gnome
```

This is from the
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

package.

Thanks to Chris Cheney for the fix over IRC

---

