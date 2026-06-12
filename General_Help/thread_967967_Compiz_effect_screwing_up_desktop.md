---
title: "Compiz effect screwing up desktop"
date: 2008-11-02
forum: General Help
---

### Post by tjenn on 2008-11-02
Hi,

I was playing around with the Compiz effects and tried one of the zoom features. It has now made my desktop messed up. I can faintly see the desktop and my task bar is smaller with lines going across it. It almost looks like it is set at the wrong refresh rate or something. I have tried booting into recovery mode and trying to disable compiz and even tried the fix the x server. Nothing worked. How can I disable or turn off compiz from loading so I can disable the problematic effect?

---

### Post by sdowney717 on 2008-11-02
you can try uninstalling compiz
boot into a console prompt

perhaps try something like this
sudo apt-get remove compiz-core

apt-get remove --purge <package>
will remove everything to do with the package

then see if it boots up without compiz running

---

### Post by tjenn on 2008-11-02
Thanks sdowney717! Worked like a charm. :)

---

