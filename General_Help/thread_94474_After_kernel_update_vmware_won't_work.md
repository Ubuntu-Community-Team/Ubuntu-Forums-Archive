---
title: "After kernel update vmware won't work"
date: 2005-11-24
forum: General Help
---

### Post by maltje on 2005-11-24
What can I do?
Do I need to install vmware again??

---

### Post by MartinG on 2005-11-24
You don't need a full re-install, but you do need to run vmware-config.pl again (or runme.pl in vmware-any-any-update93) with the new kernel's headers. And don't forget the CC=gcc-3.4 pre-amble.

---

