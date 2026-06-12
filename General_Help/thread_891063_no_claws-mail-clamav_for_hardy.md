---
title: "no claws-mail-clamav for hardy?"
date: 2008-08-15
forum: General Help
---

### Post by moore.bryan on 2008-08-15
checked the repos and claws-mail-clamav is there for gutsy, but not hardy... anyone know what the deal is?

---

### Post by colinleroy on 2008-08-24
It's been removed upstream due to a license violation. Claws Mail switched to GPL v3 at the 3.0.0 release, and at the time the libclamav we used was licensed under GPL2 or later, which was fine. Unfortunately, after Sourcefire bought Clamav, they changed the licence to GPL2 strict, which is incompatible with GPL3. Hence, the Claws developers dropped the clamav plugin.

---

### Post by moore.bryan on 2008-08-24
got it. no reconciliation in-sight?

---

