---
title: "X packages can be updated: what to do?"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by mrcoulson on 2009-09-17
I'm new to Linux.  If you've helped me before, you know that.  Anyway, I sometimes see a message like "3 packages can be updated".  What do I do about that?  Can I run something that will update them?  Does apt-get update do it or do I need to do something else?

Jeremy

---

### Post by Paresh on 2009-09-17
from a terminal, type
```
sudo apt-get update && sudo apt-get upgrade
```
and enter your password when asked

this runs two commands:-
  update will update your sources and make sure they point to the latest packages available in teh repositories
  upgrade will update your packages where necessary

Alternatively, you can use the system update

---

### Post by mrcoulson on 2009-09-17
Hey, that did something!  Thanks!  Man, I'd be lost without the Ubuntu community.

Jeremy

---

