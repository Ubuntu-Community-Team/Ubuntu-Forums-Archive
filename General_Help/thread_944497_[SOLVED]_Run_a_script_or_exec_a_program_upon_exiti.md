---
title: "[SOLVED] Run a script or exec a program upon exiting console?"
date: 2008-10-11
forum: General Help
---

### Post by Krupski on 2008-10-11
The title says it.

Is this possible? Is there some kind of script that is run AFTER a console session is run?

That is, if I run a terminal, then exit it, is there some script that runs AT EXIT, but before it's gone?

What I want to do is modify the command history list file JUST AFTER a console session is ended.

Any ideas?

Thanks!

-- Roger

---

### Post by Sam on 2008-10-11
Edit ~/.bash_logout and add whatever you want inside.

---

### Post by Krupski on 2008-10-11
> **Sam said:**
> Edit ~/.bash_logout and add whatever you want inside.

AWESOME! That's what I needed! Thanks!

-- Roger

---

