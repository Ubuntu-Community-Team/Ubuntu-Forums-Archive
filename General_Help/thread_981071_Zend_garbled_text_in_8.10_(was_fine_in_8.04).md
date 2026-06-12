---
title: "Zend garbled text in 8.10 (was fine in 8.04)"
date: 2008-11-13
forum: General Help
---

### Post by gmarton on 2008-11-13
Upgraded to 8.10 and long scripts (1000 lines+) get garbled in Zend Studio 5.5 
Tried the following
[LIST]
[*]Use another java install
[*]Added new user with fresh home directory
[*]Re-installed zend
[*]Changed fonts/sizes
[*]Switched to xubuntu-desktop
[/LIST]

Someone had issue a while back on Fedora:
[http://www.zend.com/forums/index.php?t=tree&th=6427&S=8e4dc3fa34d51c7a2dd9acfbbf7a97e5](http://www.zend.com/forums/index.php?t=tree&th=6427&S=8e4dc3fa34d51c7a2dd9acfbbf7a97e5)

Does anyone know of a fix?

---

### Post by hplehn on 2008-11-19
I have the same problem. Tried to disable glx/dri and to use awt-Toolkit as suggested in Zend forums. Graphics driver is "intel".

Zend Studio remains unusable in Intrepid.

---

### Post by chmac on 2008-11-29
I think I found a fix. I've posted the full info here:
[http://www.callum-macdonald.com/2008/11/29/zend-studio-garbled-chars-fix/](http://www.callum-macdonald.com/2008/11/29/zend-studio-garbled-chars-fix/)

---

### Post by hplehn on 2008-11-29
Fix seems to work for me.

Thanks to chmac!

---

