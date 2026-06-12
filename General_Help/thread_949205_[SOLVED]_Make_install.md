---
title: "[SOLVED] Make install"
date: 2008-10-15
forum: General Help
---

### Post by kerryhall on 2008-10-15
If I make install something, how do I remove it again?

---

### Post by Ayuthia on 2008-10-15
Have you tried sudo make uninstall?

---

### Post by Yellow Pasque on 2008-10-15
For the next time you go to build software, use checkinstall and it will make life easy if you need to uninstall.
```
sudo apt-get install checkinstall
```
[http://wiki.debian.org/CheckInstall](http://wiki.debian.org/CheckInstall)

---

### Post by kerryhall on 2008-10-16
Thanks to both of you! I am assuming that it's the developers responsibility to have "make uninstall" do something if "make install" does something.

---

