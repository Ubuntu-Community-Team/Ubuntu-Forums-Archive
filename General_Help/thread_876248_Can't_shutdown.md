---
title: "Can't shutdown"
date: 2008-07-31
forum: General Help
---

### Post by Ataris on 2008-07-31
I can open the shutdown actions dialogue but when I click on shutdown, all of the applications disappear, bla bla, but then nothing happens. The desktop is still there, but when I try to click on anything I can't, and I'm forced to do a hard shutdown.

can hard shutdowns in linux hurt anything?

---

### Post by kuja on 2008-07-31
Probably at least some risk of filesystem corruption. You obviously lose everything that was open. 

Try shutting down with the ```
shutdown -h now
``` in a shell and see if it behaves differently.

---

### Post by Ataris on 2008-07-31
Okay, but I'll have to get back to you later. Thanks.

---

