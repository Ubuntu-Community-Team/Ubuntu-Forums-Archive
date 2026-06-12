---
title: "how to uninstall OpenOffice 3 beta?"
date: 2008-09-16
forum: General Help
---

### Post by grw on 2008-09-16
Hi, 
Can anyone tell me how to uninstall Openoffice 3? Help much appreciated.
Thanks
Gwyn

I installed the deb package with this command: sudo dpkg -i *.deb

But OOo3 doesn't work at all on my old laptop, so I tried to uninstall it like this:  sudo dpkg -r openoffice.org3

I got this message:

dpkg: dependency problems prevent removal of openoffice.org3:
 openoffice.org3-impress depends on openoffice.org3.
 openoffice.org3-writer depends on openoffice.org3.
 openoffice.org3-dict-en depends on openoffice.org3.
 openoffice.org3-dict-es depends on openoffice.org3.
 openoffice.org3-draw depends on openoffice.org3.
 openoffice.org3-en-us depends on openoffice.org3.
 openoffice.org3-base depends on openoffice.org3.
 openoffice.org3-math depends on openoffice.org3.
 openoffice.org3-calc depends on openoffice.org3.
 openoffice.org3-dict-fr depends on openoffice.org3.
dpkg: error processing openoffice.org3 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 openoffice.org3

---

### Post by northern lights on 2008-09-16
```
sudo dpkg --purge --force-all openoffice.org3*
```should do the trick

---

### Post by jespdj on 2008-09-16
Read this: [Test Drive OpenOffice 3 Release Candidate 1](http://tombuntu.com/index.php/2008/09/11/test-drive-openoffice-3-release-candidate-1/)

Includes instructions on how to uninstall it.

---

### Post by grw on 2008-09-16
Thanks. Second option seemed to work

---

