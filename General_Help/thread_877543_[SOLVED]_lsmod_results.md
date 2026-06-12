---
title: "[SOLVED] lsmod results"
date: 2008-08-01
forum: General Help
---

### Post by rtrdom on 2008-08-01
While troubleshooting a network problem one sometimes needs to use lsmod.
The results in Hardy are in three columns...Module, Size, Used by. 
Is this correct or is it four columns...Module, Size, Used and by?
Additionally, what does the column "Used" mean since it is all numbers?

---

### Post by Taxman415a on 2008-08-01
lsmod's is a singularly useless manpage otherwise I would send you to man lsmod. Any self respecting manpage would give you that information. Luckily google helped in this case; "lsmod columns" found: [http://www.linuxquestions.org/questions/linux-software-2/lsmods-used-by-column-explanation-614523/](http://www.linuxquestions.org/questions/linux-software-2/lsmods-used-by-column-explanation-614523/)
which says the number is how many modules use or depend on that one and the by is the name of those modules.

---

### Post by rtrdom on 2008-08-01
Thanks taxman415a. I should have thought of google but after working on
two other networks most of the past 8 hours my mind is about empty.
I do appreciate the help and will mark this solved.

---

### Post by Taxman415a on 2008-08-01
You're very welcome. We've all been there.

---

