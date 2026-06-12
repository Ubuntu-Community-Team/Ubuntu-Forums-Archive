---
title: "[SOLVED] Gimp problems"
date: 2008-08-01
forum: General Help
---

### Post by BUSHYBOB on 2008-08-01
I just tried to run Gimp and got this error message -


The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.4.2, but the
libgimp version is 2.4.6.

How can I fix this?

---

### Post by JangMunho on 2008-08-01
It seems that you have to reinstall Gimp, because it detected a wrong version of libgimp.
Try
sudo apt-get remove --purge gimp
And then
sudo apt-get install gimp

---

### Post by BUSHYBOB on 2008-08-01
I tried that and it didn't work, however removing libgimp with synaptic, which removed gimp and xsane as well did the trick once I'd reinstalled gimp. Now to reinstall xsane.

---

