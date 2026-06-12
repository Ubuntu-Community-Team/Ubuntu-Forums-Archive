---
title: "User, root environments"
date: 2008-10-19
forum: General Help
---

### Post by reglacken on 2008-10-19
There are evidently several environments, but I can see only mine and root's, when in a root terminal. But, within a program, evidently a third environment is used.

Specifically, I want the LINES and COLUMNS of my current window within a program, but getenv("LINES") or getenv("COLUMNS") always return null; while other env vaiables work fine. By the way, echo $LINES etc work.

Is there a solution to this problem ?

---

