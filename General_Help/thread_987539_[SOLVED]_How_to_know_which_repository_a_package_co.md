---
title: "[SOLVED] How to know which repository a package comes from?"
date: 2008-11-19
forum: General Help
---

### Post by vertigo23 on 2008-11-19
Is there any way to find out ahead of time which apt repository (main, universe, multiverse, etc) a package comes from?  Besides searching packages.ubuntu.com that is.

---

### Post by drs305 on 2008-11-19
In synaptic, you can highlight the package and select Properties. It will specify universe, multiverse, etc. If there isn't a notation I believe that means it is in 'main'.

You can also use "aptitude show *packagename*" and look in 'Section'.

---

