---
title: "[SOLVED] Cleaning up after python upgrade."
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2009-01-11
I just downloaded python3.0 via apt, but I'm not sure I understand how to uninstall (and preferably remove) the previous version(s). For some reason, there seems to be versions 2.4, 2.5 which is active, and the newly installed 3.0.

Please help me understand the most efficient way to clean this up.

---

### Post by Tim Sharitt on 2009-01-11
You probably don't want ot remove the active yersion of python as python 3.0 isn't completly backwards compatable with the previous version. It is very likely that there are several applications which depend on python 2.5. Python 2.4 might be safe to remove via your prefered package manager, but there may still be applications which depend on it as well.

---

### Post by sp0nge on 2009-01-12
Good advice, something I didn't even think about.

---

