---
title: "Interpid proposed and backports"
date: 2008-11-20
forum: General Help
---

### Post by pjalegria on 2008-11-20
Should i enable this repositories???

---

### Post by Nepherte on 2008-11-20
I strongly advise not to enable the proposed repository. They are basically meant for testing purposes and might break your system. Backports is generally not a problem.

---

### Post by drs305 on 2008-11-20
The backports are generally not as stable as security, updates, or proposed, according to the community link for backports:
[UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

A more general ubuntu community link explaining the repositories is:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Unless you have a need for something in the backports or proposed repositories I would not enable them. If you do need a specific package, enable the repository, get the package, and then disable it again. Of course doing this would prevent updates to that specific package as long as it's repository is disabled.

---

