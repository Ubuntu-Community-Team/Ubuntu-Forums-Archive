---
title: "[SOLVED] Intrepid Ibex to Hardy Heron Downgrade Question"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by bedhead75 on 2008-12-12
I would like to downgrade to Hardy from Intrepid.  My home folder is in a separate partition, and from what I understand, I can do a clean install of Hardy without erasing it.  My question is this...if I do a clean install, should I also manually delete all of the hidden folders such as ".evolution", ".mozilla", ".opera" in the home folder so that I don't get any conficts between existing program configuration once I switch back to Hardy, since earlier versions of those programs (i.e. Pidgin 2.5.2 in Ibex vs. Pidgin 2.4.1 in Heron) are associated with Hardy?  I'm using 64-bit by the way.

---

### Post by aysiu on 2008-12-12
No, you shouldn't delete all those hidden folders. Having those hidden folders intact is the main point of having a separate /home partition.

If you do discover some kind of configuration glitch, you can always delete the folder after reinstalling Hardy.

---

